Table Etl.DataSource {#tblEtlDataSource}
--------------------

Description:

Etl table containing list of avaliable data sources.

  ----------------------------------------------------------------------------------
  Id   Column Name                Data Type       Allow   Description
                                                  Nulls   
  ---- -------------------------- --------------- ------- --------------------------
  1    DataSourceId               int             Yes     Id of the data source for
                                                          unique identification of
                                                          the data source across the
                                                          data warehouse

  2    Name                       nvarchar(510)   Yes     Human understandable name
                                                          of the data source

  3    DataSourceTypeId           int             Yes     Id defining the type of
                                                          givrn dta source (SQL,
                                                          ...)

  4    Server                     nvarchar(510)   Yes     Source database server
                                                          name (linked server name)

  5    Database                   nvarchar(510)   Yes     Source database name
  ----------------------------------------------------------------------------------

\[Back to table list\]\[listoftables\]
