# Vagrant-PySpark

Vagrant-PySpark is a Vagrant box that can be provisioned with any Spark 
version, ready to run Spark jobs (included PySpark) and unit testing for
PySpark.

It is intended to be used only for development and testing with small data sets.

## Set up

To start and provision the vagrant box you must set a file (**ansible/variables.yml**)
with required variables:

* Scala version
* Spark version
* Hadoop version

Versions must match with the one provided here:

* For Scala: https://www.scala-lang.org/download/
* For Spark and Hadoop: http://spark.apache.org/downloads.html

Variable file should contain following variables:

```yml
scala:
  version: 2.11.8
spark:
  version: 2.3.1
hadoop:
  version: 2.7
```

You can find examples for Spark 1.6.3 and 2.1.0 in this repo:

* [ansible/vars/vars_spark_1.6.3.yml](ansible/vars/vars_spark_1.6.3.yml)
* [ansible/vars/vars_spark_2.1.0.yml](ansible/vars/vars_spark_2.1.0.yml)

You can create a symbolic link to use them:

```bash
ln -s vars/vars_spark_2.1.0.yml ansible/variables.yml
```

If you use other versions, PRs are welcome with your version setup.

## Required

* [Vagrant](https://www.vagrantup.com/)

## How to use

### Clone your projects
Set up the Vagrant box and clone your projects inside to run your jobs and tests.

### Sync you projects folder
You can fork this repo and extend the Vagrant file to sync your projects
folder in the Vagrant box. It will allow you to have all your changes immediately
available to run in the Vagrant box.

```ruby
config.vm.synced_folder "/Project/path/in/host/machine", "/Destination/in/vagrant/box"
```

```
vagrant up
```

### Running PySpark

```
    $ PYSPARK_PYTHON=python3 pyspark
```

### Running Jupyter

```
    $ jupyter notebook --no-browser
```

Since we installed `findspark`, we can start a new iPython notebook and run PySpark as follows:

```
    import findspark
    findspark.init()

    import pyspark
```

## PySpark Unit Testing

You can find good explanation and examples [here](https://github.com/kawadia/pyspark.test)


## Bugs

If you can't get Vagrant's port forwarding to work, use an SSH tunnel:

```
vagrant ssh-config > vagrant-ssh-config
ssh -L 8888:127.0.0.1:8888 -F vagrant-ssh-config pyspark-box

```
