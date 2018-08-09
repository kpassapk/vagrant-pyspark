# Vagrant-PySpark

## Nueva instalación

```
    vagrant up
    vagrant package
    vagrant box add pyspark-box package.box

```

## Obtener cambios de "upstream"


```
   git fetch origin master
   vagrant destroy
   vagrant box remove pyspark-box
   vagrant up
   vagrant package
   vagrant box add pyspark-box package.box
   
```
