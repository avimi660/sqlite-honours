`` # dump file we used was not understandable by sqlite3 so we had to convert to sqlite 3 format 
` # used online tool which converts the file for us
wget https://github.com/caiiiycuk/postgresql-to-sqlite/releases/download/1.0/pg2sqlite.jar

# then we can use it 
java -jar pg2sqlite.jar -d mitoproteome_dump.sql -o mitosqlite.db

# then within sqlite (by typing sqlite3) these next three lines open ip the database. .tables lists the various tables, and because mt_gene looks like a goer we used .schema to look at the bits in mt_gene

.open mito_sqlite.db
.tables
.schema mt_gene

# to pull out the gene names and put them into a file called mito_genes.txt, we want headers, and tab delimited 
.header on
.mode tabs
.output mito_genes.txt
SELECT * FROM mito_genes;
