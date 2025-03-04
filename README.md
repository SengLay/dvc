# DVC - Data Version Control

## 1. Setting up
`Python 3.10.x` is used in this `DVC` tryout.

* Using following command for setting up virtual environment
    ```bash
    python3.10 venv venv
    source venv/bin/activate
    ```

* Install DVC [^2]:
    ```bash
    pip install dvc
    ```

## 2. Initialize Git and DVC (From this below [^1])
```bash
git init
dvc init
```

## 3. Tracking data
Assume that `data/` is our actual data directory.

```bash
dvc add data/data.xml
git add data/data.xml.dvc data/.gitignore
```

## 4. Storing and Sharing
```bash
mkdir tmp/dvcstore
dvc remote add -d myremote dvcstore/
```

> [!NOTE]  
> DVC supports many remote storage types, including **Amazon S3**, **NFS**, **SSH**, **Google Drive**, **Azure Blob Storage**, and **HDFS**.
> ```bash
> dvc remote add -d storage s3://mybucket/dvcstore
> ```
> To learn more about storage remotes, see the [Remote Storage Guide](https://dvc.org/doc/user-guide/data-management/remote-storage).


## 5. Uploading
```bash
dvc push
git push
```

## 6. Retrieving
```bash
dvc pull
```
> [!IMPORTANT]
> * The project's `data/data.xml` file, our cache and the remote storage were all already in sync.
> * We need to **EMPTY** the **cache** and delete `data/data.xml` from our project if we want to have DVC actually moving data around.

* For Mac:
    ```bash
    rm -rf .dvc/cache
    rm -f data/data.xml
    ```
* For Window:
    ```bash
    rmdir .dvc\cache
    del data\data.xml
    ```

* Then, 
    ```bash
    dvc pull
    ```

# References
[^1]: https://dvc.org/doc/start?tab=Windows-Cmd-#expand-to-simulate-a-fresh-pull
[^2]: https://pypi.org/project/dvc/