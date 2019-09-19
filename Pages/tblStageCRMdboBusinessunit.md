Table Stage.CRMdboBusinessunit {#tblStageCRMdboBusinessunit}
------------------------------

Description:

Stage table CRMdboBusinessunit.

List of dependent objects:

-   \[Stage.uspLoadCRMdboBusinessunit\]\[spStageuspLoadCRMdboBusinessunit\]

-   \[Vault.uspLoadCRMdboBusinessunit\]\[spVaultuspLoadCRMdboBusinessunit\]

  ----------------------------------------------------------------------------------------------------------------------
  Id    Column Name                                Data Type          Allow   Description
                                                                      Nulls   
  ----- ------------------------------------------ ------------------ ------- ------------------------------------------
  1     address1\_addressid                        uniqueidentifier   Yes     Column address1\_addressid from
                                                                              ScaniaCRMExport.dbo.businessunit

  2     address1\_addresstypecode                  int                Yes     Column address1\_addresstypecode from
                                                                              ScaniaCRMExport.dbo.businessunit

  3     address1\_city                             nvarchar(320)      Yes     Column address1\_city from
                                                                              ScaniaCRMExport.dbo.businessunit

  4     address1\_country                          nvarchar(320)      Yes     Column address1\_country from
                                                                              ScaniaCRMExport.dbo.businessunit

  5     address1\_county                           nvarchar(200)      Yes     Column address1\_county from
                                                                              ScaniaCRMExport.dbo.businessunit

  6     address1\_fax                              nvarchar(200)      Yes     Column address1\_fax from
                                                                              ScaniaCRMExport.dbo.businessunit

  7     address1\_latitude                         decimal            Yes     Column address1\_latitude from
                                                                              ScaniaCRMExport.dbo.businessunit

  8     address1\_line1                            nvarchar(1000)     Yes     Column address1\_line1 from
                                                                              ScaniaCRMExport.dbo.businessunit

  9     address1\_line2                            nvarchar(1000)     Yes     Column address1\_line2 from
                                                                              ScaniaCRMExport.dbo.businessunit

  10    address1\_line3                            nvarchar(1000)     Yes     Column address1\_line3 from
                                                                              ScaniaCRMExport.dbo.businessunit

  11    address1\_longitude                        decimal            Yes     Column address1\_longitude from
                                                                              ScaniaCRMExport.dbo.businessunit

  12    address1\_name                             nvarchar(400)      Yes     Column address1\_name from
                                                                              ScaniaCRMExport.dbo.businessunit

  13    address1\_postalcode                       nvarchar(80)       Yes     Column address1\_postalcode from
                                                                              ScaniaCRMExport.dbo.businessunit

  14    address1\_postofficebox                    nvarchar(80)       Yes     Column address1\_postofficebox from
                                                                              ScaniaCRMExport.dbo.businessunit

  15    address1\_shippingmethodcode               int                Yes     Column address1\_shippingmethodcode from
                                                                              ScaniaCRMExport.dbo.businessunit

  16    address1\_stateorprovince                  nvarchar(200)      Yes     Column address1\_stateorprovince from
                                                                              ScaniaCRMExport.dbo.businessunit

  17    address1\_telephone1                       nvarchar(200)      Yes     Column address1\_telephone1 from
                                                                              ScaniaCRMExport.dbo.businessunit

  18    address1\_telephone2                       nvarchar(200)      Yes     Column address1\_telephone2 from
                                                                              ScaniaCRMExport.dbo.businessunit

  19    address1\_telephone3                       nvarchar(200)      Yes     Column address1\_telephone3 from
                                                                              ScaniaCRMExport.dbo.businessunit

  20    address1\_upszone                          nvarchar(16)       Yes     Column address1\_upszone from
                                                                              ScaniaCRMExport.dbo.businessunit

  21    address1\_utcoffset                        int                Yes     Column address1\_utcoffset from
                                                                              ScaniaCRMExport.dbo.businessunit

  22    address2\_addressid                        uniqueidentifier   Yes     Column address2\_addressid from
                                                                              ScaniaCRMExport.dbo.businessunit

  23    address2\_addresstypecode                  int                Yes     Column address2\_addresstypecode from
                                                                              ScaniaCRMExport.dbo.businessunit

  24    address2\_city                             nvarchar(320)      Yes     Column address2\_city from
                                                                              ScaniaCRMExport.dbo.businessunit

  25    address2\_country                          nvarchar(320)      Yes     Column address2\_country from
                                                                              ScaniaCRMExport.dbo.businessunit

  26    address2\_county                           nvarchar(200)      Yes     Column address2\_county from
                                                                              ScaniaCRMExport.dbo.businessunit

  27    address2\_fax                              nvarchar(200)      Yes     Column address2\_fax from
                                                                              ScaniaCRMExport.dbo.businessunit

  28    address2\_latitude                         decimal            Yes     Column address2\_latitude from
                                                                              ScaniaCRMExport.dbo.businessunit

  29    address2\_line1                            nvarchar(1000)     Yes     Column address2\_line1 from
                                                                              ScaniaCRMExport.dbo.businessunit

  30    address2\_line2                            nvarchar(1000)     Yes     Column address2\_line2 from
                                                                              ScaniaCRMExport.dbo.businessunit

  31    address2\_line3                            nvarchar(1000)     Yes     Column address2\_line3 from
                                                                              ScaniaCRMExport.dbo.businessunit

  32    address2\_longitude                        decimal            Yes     Column address2\_longitude from
                                                                              ScaniaCRMExport.dbo.businessunit

  33    address2\_name                             nvarchar(400)      Yes     Column address2\_name from
                                                                              ScaniaCRMExport.dbo.businessunit

  34    address2\_postalcode                       nvarchar(80)       Yes     Column address2\_postalcode from
                                                                              ScaniaCRMExport.dbo.businessunit

  35    address2\_postofficebox                    nvarchar(80)       Yes     Column address2\_postofficebox from
                                                                              ScaniaCRMExport.dbo.businessunit

  36    address2\_shippingmethodcode               int                Yes     Column address2\_shippingmethodcode from
                                                                              ScaniaCRMExport.dbo.businessunit

  37    address2\_stateorprovince                  nvarchar(200)      Yes     Column address2\_stateorprovince from
                                                                              ScaniaCRMExport.dbo.businessunit

  38    address2\_telephone1                       nvarchar(200)      Yes     Column address2\_telephone1 from
                                                                              ScaniaCRMExport.dbo.businessunit

  39    address2\_telephone2                       nvarchar(200)      Yes     Column address2\_telephone2 from
                                                                              ScaniaCRMExport.dbo.businessunit

  40    address2\_telephone3                       nvarchar(200)      Yes     Column address2\_telephone3 from
                                                                              ScaniaCRMExport.dbo.businessunit

  41    address2\_upszone                          nvarchar(16)       Yes     Column address2\_upszone from
                                                                              ScaniaCRMExport.dbo.businessunit

  42    address2\_utcoffset                        int                Yes     Column address2\_utcoffset from
                                                                              ScaniaCRMExport.dbo.businessunit

  43    businessunitid                             uniqueidentifier   Yes     Column businessunitid from
                                                                              ScaniaCRMExport.dbo.businessunit

  44    calendarid                                 uniqueidentifier   Yes     Column calendarid from
                                                                              ScaniaCRMExport.dbo.businessunit

  45    calendarid\_entitytype                     nvarchar(512)      Yes     Column calendarid\_entitytype from
                                                                              ScaniaCRMExport.dbo.businessunit

  46    costcenter                                 nvarchar(400)      Yes     Column costcenter from
                                                                              ScaniaCRMExport.dbo.businessunit

  47    createdby                                  uniqueidentifier   Yes     Column createdby from
                                                                              ScaniaCRMExport.dbo.businessunit

  48    createdby\_entitytype                      nvarchar(512)      Yes     Column createdby\_entitytype from
                                                                              ScaniaCRMExport.dbo.businessunit

  49    createdbyname                              nvarchar(400)      Yes     Column createdbyname from
                                                                              ScaniaCRMExport.dbo.businessunit

  50    createdbyyominame                          nvarchar(400)      Yes     Column createdbyyominame from
                                                                              ScaniaCRMExport.dbo.businessunit

  51    createdon                                  datetime           Yes     Column createdon from
                                                                              ScaniaCRMExport.dbo.businessunit

  52    createdonbehalfby                          uniqueidentifier   Yes     Column createdonbehalfby from
                                                                              ScaniaCRMExport.dbo.businessunit

  53    createdonbehalfby\_entitytype              nvarchar(512)      Yes     Column createdonbehalfby\_entitytype from
                                                                              ScaniaCRMExport.dbo.businessunit

  54    createdonbehalfbyname                      nvarchar(400)      Yes     Column createdonbehalfbyname from
                                                                              ScaniaCRMExport.dbo.businessunit

  55    createdonbehalfbyyominame                  nvarchar(400)      Yes     Column createdonbehalfbyyominame from
                                                                              ScaniaCRMExport.dbo.businessunit

  56    creditlimit                                decimal            Yes     Column creditlimit from
                                                                              ScaniaCRMExport.dbo.businessunit

  57    description                                nvarchar(max)      Yes     Column description from
                                                                              ScaniaCRMExport.dbo.businessunit

  58    disabledreason                             nvarchar(2000)     Yes     Column disabledreason from
                                                                              ScaniaCRMExport.dbo.businessunit

  59    divisionname                               nvarchar(400)      Yes     Column divisionname from
                                                                              ScaniaCRMExport.dbo.businessunit

  60    emailaddress                               nvarchar(400)      Yes     Column emailaddress from
                                                                              ScaniaCRMExport.dbo.businessunit

  61    exchangerate                               decimal            Yes     Column exchangerate from
                                                                              ScaniaCRMExport.dbo.businessunit

  62    fileasname                                 nvarchar(400)      Yes     Column fileasname from
                                                                              ScaniaCRMExport.dbo.businessunit

  63    ftpsiteurl                                 nvarchar(800)      Yes     Column ftpsiteurl from
                                                                              ScaniaCRMExport.dbo.businessunit

  64    Id                                         uniqueidentifier   Yes     Column Id from
                                                                              ScaniaCRMExport.dbo.businessunit

  65    importsequencenumber                       int                Yes     Column importsequencenumber from
                                                                              ScaniaCRMExport.dbo.businessunit

  66    inheritancemask                            int                Yes     Column inheritancemask from
                                                                              ScaniaCRMExport.dbo.businessunit

  67    isdisabled                                 bit                Yes     Column isdisabled from
                                                                              ScaniaCRMExport.dbo.businessunit

  68    llp\_countryid                             uniqueidentifier   Yes     Column llp\_countryid from
                                                                              ScaniaCRMExport.dbo.businessunit

  69    llp\_countryid\_entitytype                 nvarchar(512)      Yes     Column llp\_countryid\_entitytype from
                                                                              ScaniaCRMExport.dbo.businessunit

  70    llp\_countryidname                         nvarchar(400)      Yes     Column llp\_countryidname from
                                                                              ScaniaCRMExport.dbo.businessunit

  71    llp\_iddealernr                            int                Yes     Column llp\_iddealernr from
                                                                              ScaniaCRMExport.dbo.businessunit

  72    llp\_idnetsuite                            int                Yes     Column llp\_idnetsuite from
                                                                              ScaniaCRMExport.dbo.businessunit

  73    llp\_isworkshop                            bit                Yes     Column llp\_isworkshop from
                                                                              ScaniaCRMExport.dbo.businessunit

  74    llp\_teamid                                uniqueidentifier   Yes     Column llp\_teamid from
                                                                              ScaniaCRMExport.dbo.businessunit

  75    llp\_teamid\_entitytype                    nvarchar(512)      Yes     Column llp\_teamid\_entitytype from
                                                                              ScaniaCRMExport.dbo.businessunit

  76    llp\_teamidname                            nvarchar(640)      Yes     Column llp\_teamidname from
                                                                              ScaniaCRMExport.dbo.businessunit

  77    llp\_teamidyominame                        nvarchar(640)      Yes     Column llp\_teamidyominame from
                                                                              ScaniaCRMExport.dbo.businessunit

  78    llp\_utapprovaltemplateid                  uniqueidentifier   Yes     Column llp\_utapprovaltemplateid from
                                                                              ScaniaCRMExport.dbo.businessunit

  79    llp\_utapprovaltemplateid\_entitytype      nvarchar(512)      Yes     Column
                                                                              llp\_utapprovaltemplateid\_entitytype from
                                                                              ScaniaCRMExport.dbo.businessunit

  80    llp\_utapprovaltemplateidname              nvarchar(400)      Yes     Column llp\_utapprovaltemplateidname from
                                                                              ScaniaCRMExport.dbo.businessunit

  81    llp\_utreservationapproverid               uniqueidentifier   Yes     Column llp\_utreservationapproverid from
                                                                              ScaniaCRMExport.dbo.businessunit

  82    llp\_utreservationapproverid\_entitytype   nvarchar(512)      Yes     Column
                                                                              llp\_utreservationapproverid\_entitytype
                                                                              from ScaniaCRMExport.dbo.businessunit

  83    llp\_utreservationapproveridname           nvarchar(800)      Yes     Column llp\_utreservationapproveridname
                                                                              from ScaniaCRMExport.dbo.businessunit

  84    llp\_utreservationapproveridyominame       nvarchar(800)      Yes     Column
                                                                              llp\_utreservationapproveridyominame from
                                                                              ScaniaCRMExport.dbo.businessunit

  85    modifiedby                                 uniqueidentifier   Yes     Column modifiedby from
                                                                              ScaniaCRMExport.dbo.businessunit

  86    modifiedby\_entitytype                     nvarchar(512)      Yes     Column modifiedby\_entitytype from
                                                                              ScaniaCRMExport.dbo.businessunit

  87    modifiedbyname                             nvarchar(400)      Yes     Column modifiedbyname from
                                                                              ScaniaCRMExport.dbo.businessunit

  88    modifiedbyyominame                         nvarchar(400)      Yes     Column modifiedbyyominame from
                                                                              ScaniaCRMExport.dbo.businessunit

  89    modifiedon                                 datetime           Yes     Column modifiedon from
                                                                              ScaniaCRMExport.dbo.businessunit

  90    modifiedonbehalfby                         uniqueidentifier   Yes     Column modifiedonbehalfby from
                                                                              ScaniaCRMExport.dbo.businessunit

  91    modifiedonbehalfby\_entitytype             nvarchar(512)      Yes     Column modifiedonbehalfby\_entitytype from
                                                                              ScaniaCRMExport.dbo.businessunit

  92    modifiedonbehalfbyname                     nvarchar(400)      Yes     Column modifiedonbehalfbyname from
                                                                              ScaniaCRMExport.dbo.businessunit

  93    modifiedonbehalfbyyominame                 nvarchar(400)      Yes     Column modifiedonbehalfbyyominame from
                                                                              ScaniaCRMExport.dbo.businessunit

  94    name                                       nvarchar(640)      Yes     Column name from
                                                                              ScaniaCRMExport.dbo.businessunit

  95    organizationid                             uniqueidentifier   Yes     Column organizationid from
                                                                              ScaniaCRMExport.dbo.businessunit

  96    organizationid\_entitytype                 nvarchar(512)      Yes     Column organizationid\_entitytype from
                                                                              ScaniaCRMExport.dbo.businessunit

  97    organizationidname                         nvarchar(400)      Yes     Column organizationidname from
                                                                              ScaniaCRMExport.dbo.businessunit

  98    overriddencreatedon                        datetime           Yes     Column overriddencreatedon from
                                                                              ScaniaCRMExport.dbo.businessunit

  99    parentbusinessunitid                       uniqueidentifier   Yes     Column parentbusinessunitid from
                                                                              ScaniaCRMExport.dbo.businessunit

  100   parentbusinessunitid\_entitytype           nvarchar(512)      Yes     Column parentbusinessunitid\_entitytype
                                                                              from ScaniaCRMExport.dbo.businessunit

  101   parentbusinessunitidname                   nvarchar(400)      Yes     Column parentbusinessunitidname from
                                                                              ScaniaCRMExport.dbo.businessunit

  102   picture                                    nvarchar(max)      Yes     Column picture from
                                                                              ScaniaCRMExport.dbo.businessunit

  103   SinkCreatedOn                              datetime           Yes     Column SinkCreatedOn from
                                                                              ScaniaCRMExport.dbo.businessunit

  104   SinkModifiedOn                             datetime           Yes     Column SinkModifiedOn from
                                                                              ScaniaCRMExport.dbo.businessunit

  105   stockexchange                              nvarchar(80)       Yes     Column stockexchange from
                                                                              ScaniaCRMExport.dbo.businessunit

  106   tickersymbol                               nvarchar(40)       Yes     Column tickersymbol from
                                                                              ScaniaCRMExport.dbo.businessunit

  107   transactioncurrencyid                      uniqueidentifier   Yes     Column transactioncurrencyid from
                                                                              ScaniaCRMExport.dbo.businessunit

  108   transactioncurrencyid\_entitytype          nvarchar(512)      Yes     Column transactioncurrencyid\_entitytype
                                                                              from ScaniaCRMExport.dbo.businessunit

  109   transactioncurrencyidname                  nvarchar(400)      Yes     Column transactioncurrencyidname from
                                                                              ScaniaCRMExport.dbo.businessunit

  110   usergroupid                                uniqueidentifier   Yes     Column usergroupid from
                                                                              ScaniaCRMExport.dbo.businessunit

  111   utcoffset                                  int                Yes     Column utcoffset from
                                                                              ScaniaCRMExport.dbo.businessunit

  112   versionnumber                              bigint             Yes     Column versionnumber from
                                                                              ScaniaCRMExport.dbo.businessunit

  113   websiteurl                                 nvarchar(800)      Yes     Column websiteurl from
                                                                              ScaniaCRMExport.dbo.businessunit

  114   workflowsuspended                          bit                Yes     Column workflowsuspended from
                                                                              ScaniaCRMExport.dbo.businessunit

  115   DataSourceId                               int                Yes     Id of the data source the row comes from

  116   ThreadLogId                                int                Yes     Id of ThreadLog which inserted the row
  ----------------------------------------------------------------------------------------------------------------------

\[Back to table list\]\[listoftables\]
