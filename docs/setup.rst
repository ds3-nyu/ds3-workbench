=====================================
Setup DS3 Instance and Load Test Data
=====================================


The following is a brief instruction on how to setup the DS3 Web API and load provided test data into the underlying database.



Setting up the Environment
--------------------------

Start by cloning the `DS3 Workbench Repository <https://github.com/ds3-nyu/ds3-workbench>`_ repository and all the submodules into your current working directory.

.. code-block:: console

    git clone --recursive git@github.com:ds3-nyu/ds3-workbench.git


We recommend using a virtual environment, either using `virtualenv <https://virtualenv.pypa.io/en/stable/>`_ or `Anaconda <https://www.anaconda.com/>`_. For `virtualenv` you can use the following commands:

.. code-block:: console

    # -- Create a new virtual environment
    virtualenv venv
    # -- Activate the virtual environment
    source venv/bin/activate

For setting up a virtual environment in `conda` you can use these commands:

.. code-block:: console

    # -- Create a new virtual environment
    conda create -n ds3 pip
    # -- Activate the virtual environment
    conda activate ds3


After you have activated your virtual environment, you can install the Python modules for the DS3 Web Service.

.. code-block:: console

    pip install -e ds3-workbench/ds3-workbench-api/
    pip install -e ds3-workbench/ds3-workbench-core/



Create and Initialize the Database
----------------------------------

To use a SQLLite3 database in the local folder set the following environment variables. This will create a database file `sqlite.db` in the current folder.

.. code-block:: console

    export DS3_DATABASE=sqlite+pysqlite:///sqlite.db
    export DS3_APIPATH=/ds3/api/v1

The `postgres.rst <https://github.com/ds3-nyu/ds3-workbench-core/blob/master/docs/dev/postgres.rst>`_ document contains information on how to setup a database in PostgreSQL for DS3. The environment variables should be set as follows:


.. code-block:: console

    export DS3_DATABASE=postgresql+psycopg2://user:password@localhost/database
    export DS3_APIPATH=/ds3/api/v1


The following three commands will create the database schema and load the default master data.

.. code-block:: console

    ds3adm init -f
    ds3adm load
    # -- This will load an example of the affiliation information for NYU departments
    ds3adm load -d ds3-workbench/data/setup/ -s affiliation.json


Run the Flask Web Server
------------------------

Set the following environment variables to configure the web server. The start the server.

.. code-block:: console

    export FLASK_APP=ds3api
    export FLASK_ENV=development

    flask run


Load Sample Projects and Workers
--------------------------------

In a separate terminal (but in the same working directory) run the following commands to load project and worker data (Note: Make sure to activate the virtual environment). The first command loads a list of projects. The second loads a list of workers.

.. code-block:: console

    python ds3-workbench/ds3-workbench-core/tools/load-projects.py \
        ds3-workbench/data/test/projects/ \
        http://localhost:5000/ds3/api/v1

    python ds3-workbench/ds3-workbench-core/tools/load-workers.py \
        ds3-workbench/data/test/workers/workers.tsv \
        http://localhost:5000/ds3/api/v1
