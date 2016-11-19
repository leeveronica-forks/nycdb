# nyc-db

A database chock-full of NYC housing data.

### Datasets

- pluto: 2003 - present
- DOB JOBS
- HPD Violations
- HPD Registrations
- DOF sales
- Tax Bills - rent stabilization data

### TABLES

*pluto*
 - pluto_03c
 - pluto_04c
 - pluto_05d
 - pluto_06c
 - pluto_07c
 - pluto_09v2
 - pluto_10v2
 - pluto_11v2
 - pluto_12v2
 - pluto_13v2
 - pluto_14v2
 - pluto_15v1
 - pluto_16v1
 
*dob*
 - dobjobs
 
*hpd violations*
 - violations
 - uniq_violations
 - open_violations
 - all_violations

*hpd registrations*
 - hpd.contacts
 - hpd.corporate_owners
 - hpd.registrations
 - hpd.registrations_grouped_by_bbl

*dof*
 - sales

*tax bills*
 - rentstab

### Install requirements

This will work on Debian, possibly ubuntu.

```
sudo apt install wget python3 python3-psycopg2
```

The scripts to insert the data for these datasets are scatted across different repos, each using varying languages and strategies. They are kepts as submodules in the modules/ folder: 

- [PLUTO](https://github.com/aepyornis/pluto)
- [Department of Building's Job Filings](https://github.com/aepyornis/DOB-Jobs)
- [HPD Violations](https://github.com/aepyornis/hpd-violations)
- [HPD Registrations](https://github.com/aepyornis/hpd)
- [DOF Sales](https://github.com/aepyornis/dof-sales)
- [Rent Stabilization Unit Counts](https://github.com/aepyornis/nyc-stabilization-unit-counts-to-pg)

### ENV VARS

stored in env.sh

``` sh
# postgres password
PGPASSWORD=
# define whatever psql command needed to connect to a database, which might vary depending on your setup.
# for instance: 
execute_sql () {
	psql -u username -h 127.0.0.1 -d nycdb -f $1	
}
 
NYCDB_DOBJOB_CSVPARSER="nycdb"
NYCDB_CONNECTION_STRING="dbname=nycdb user=ziggy"

# HPD REGISTRATIONS
HPD_REPO_PATH=
HPD_REGISTRATIONS_FILE=
HPD_CONTACTS_FILE=
BBL_LAT_LNG=

# DOF SALES
DOF_SALES_DATA_PATH=
DOF_SALES_REPO=

# rentstab
RENTSTAB_REPO=
RENTSTAB_FILE="/path/to/joined.csv"

```

### Datasets to add:
    - ACRIS
    - hpd complaints
    - selected 311 complaints