# HYG-Database-SQLite

This is an import of the HYG star database archive (https://github.com/astronexus/HYG-Database) into a SQLite database.

## Instructions

Initialize SQLite database file:

```bash
sqlite3 hygdata.db
```

Create the tables:

```
sqlite> .read schema/constellation.sql
sqlite> .read schema/dso.sql
sqlite> .read schema/ngc.sql
sqlite> .read schema/hygdata.sql
```

Load the data:

```
sqlite> .mode csv
sqlite> .headers off
```

```
sqlite> .import csv/constellation.csv constellation
sqlite> .import csv/dso.csv dso
sqlite> .import csv/ngc.csv ngc
sqlite> .import csv/hygdata_v3.csv hygdata
```

Retrieve some info about Orion to confirm that the data loaded successfully:

```
sqlite> .mode table
sqlite> .read scripts/orion.sql
```

```
+------------+----------------+-------------+-----------+-----------------+
| ProperName | RightAscension | Declination | Magnitude | InConstellation |
+------------+----------------+-------------+-----------+-----------------+
| Alnilam    | 84.053385      | -1.20192    | 1.69      | Orion           |
| Alnitak    | 85.189695      | -1.942572   | 1.74      | Orion           |
| Bellatrix  | 81.282765      | 6.349702    | 1.64      | Orion           |
| Betelgeuse | 88.792935      | 7.407063    | 0.45      | Orion           |
| Hatsya     | 83.858265      | -5.909901   | 2.75      | Orion           |
| Mintaka    | 83.001675      | -0.299092   | 2.25      | Orion           |
| Rigel      | 78.63447       | -8.20164    | 0.18      | Orion           |
| Saiph      | 86.939115      | -9.669605   | 2.07      | Orion           |
+------------+----------------+-------------+-----------+-----------------+
```
