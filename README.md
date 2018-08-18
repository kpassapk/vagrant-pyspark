# Vagrant-PySpark

## Nueva instalación

```

    vagrant up
    vagrant package
    vagrant box add pyspark-box package.box
    vagrant halt

```

## Obtener cambios de "upstream"

```

   git fetch origin
   vagrant destroy
   vagrant box remove pyspark-box
   vagrant up
   vagrant package
   vagrant box add pyspark-box package.box
   
```
