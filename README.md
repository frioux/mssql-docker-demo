[Long version is here](https://blog.afoolishmanifesto.com/posts/mssql-odbc-client-and-server-on-ubuntu/).

To get up and get gnarly:

1. Start the server:

`bin/server`

2. Build the client:

`docker build -t mssql-client -f Dockerfile.client.ubuntu-16-04 .`

3. Run the client:

```
$ bin/client.ubuntu-16-04 'CREATE DATABASE TheDB'`

$ bin/client.ubuntu-16-04 'USE MyDB;
   CREATE TABLE "Foo" (
      "id" int NOT NULL IDENTITY (1,1),
      "name" varchar(255) NOT NULL,
      CONSTRAINT "PK_Foo" PRIMARY KEY CLUSTERED ("id")
   )'

$ bin/client.ubuntu-16-04 'USE MyDB; INSERT INTO "Foo" (name) VALUES (?);' fREW

$ bin/client.ubuntu-16-04 --show-output 'USE MyDB; SELECT * FROM Foo WHERE name = ?' frew
$VAR1 = [
          [
            1,
            'frew'
          ]
        ];
```

4. Profit!
