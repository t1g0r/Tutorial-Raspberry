**Recover Data after an Unexpected Shutdown**

If the mongod.lock file in the data directory specified by dbPath, /data/db by default, is not a zero-byte file, then mongod will refuse to start, and you will find a message that contains the following line in your MongoDB log our output:

`Unclean shutdown detected.`

This indicates that you need to run mongod with the --repair option. If you run repair when the mongodb.lock file exists in your dbPath, or the optional --repairpath, you will see a message that contains the following line:

`old lock file: /data/db/mongod.lock. probably means unclean shutdown`

1. Remember your dbpath
2. run this command ```mongod --dbpath /your/db/path```

To repair your data files using the --repairpath option to preserve the original data files unmodified.
```mongod --dbpath /your/current/dbpath --repair --repairpath /repair/path```



ref :
- https://docs.mongodb.org/manual/tutorial/recover-data-following-unexpected-shutdown/
