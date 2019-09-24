## Takeaways
We will sometimes want to interact with our database and use its results in a specific programming language. E.g. to build web applications or data pipelines in a specific language (Ruby, Python, Javascript, etc.). That's where DBAPIs come in.

## A DBAPI
provides a standard interface for one programming language (like Python) to talk to a relational database server.
Is a low level library for writing SQL statements that connect to a database
is also known as database adapters
Different DBAPIs exist for every server framework or language + database system
Database adapters define a standard for using a database (with SQL) and using the results of database queries as input data in the given language.
Turn a selected SELECT * from some_table; list of rows into an array of objects in Javascript for say a NodeJS adapter; or a list of tuples in Python for a Python adapter.
Examples across languages and server frameworks
For Ruby (e.g. for Sinatra, Ruby on Rails): pg
For NodeJS: node-postgres
For Python (e.g. for Flask, Django): pyscopg2
psycopg2 is the focus of this course since we are using a Python stack.

## Install psycopg2
We will install pysocpg2 and use it to establish a connection to our postgres server, and interact with it in python.

psycopg2 installation steps
Follow the psycopg2 install instructions found here.

### Install Tips:

Make sure you have Python 3 version between 3.4 to 3.7. You can find out with

  $ python --version
Use the latest pip version: $ pip3 install -U pip

Replace X.Y in the export PATH... line with the version of Postgres you are using. Find out with $ postgres -V. E.g.:

  $ postgres -V
  postgres (PostgreSQL) 10.2
If the version is 10.2, then replace the X.Y in the export PATH line with 10.2:

In ~/.bash_profile or ~/.bashrc, we should add:

  export PATH=/usr/lib/postgresql/10.2/bin/:$PATH
To export and add things to your PATH, add the export PATH=.... line to either ~/.bashrc or ~/.bash_profile on your machine, e.g. with vim:

  $ vim ~/.bashrc`
  # or
  $ vim ~/.bash_profile

where you can use :w, :wq vim commands to edit your bash file and add the export PATH=... line somewhere. (See also: Vim tutorial

When you are done editing your bash profile, be sure to run source ~./bash_profile or source ~/.bashrc on your edited file, so your terminal session can grab the latest profile changes.

After editing your bash profile, you are ready to run the install step:

  $ pip install pyscopg2
A prerequisite for psycopg2 is OpenSSL. If you try installing and run into error ld: library not found for -lssl, then install openssl first.

On homebrew (for macOS or Linux): run brew install openssl (or sudo brew install openssl)
Otherwise, you can visit the OpenSSL Downloads page to download OpenSSL for your machine.
Add the LIBRARY_PATH to your bash profile:

  export LIBRARY_PATH=$LIBRARY_PATH:/usr/local/opt/openssl/lib/
Don't forget to run source ~/.bash_profile or source ~/.profile when done.

If the regular install doesn't work, you can also just install the binary version instead:

  pip install psycopg2-binary
which replaces the need to run pip install pyscopg2

Install troubleshooting threads:

For error Failed building wheel for psycopg2: https://stackoverflow.com/questions/34304833/failed-building-wheel-for-psycopg2-macosx-using-virtualenv-and-pip
For error pg_config executable not found: https://stackoverflow.com/questions/11618898/pg-config-executable-not-found
