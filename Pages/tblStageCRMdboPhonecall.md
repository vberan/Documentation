Table Stage.CRMdboPhonecall {#tblStageCRMdboPhonecall}
---------------------------

Description:

Stage table CRMdboPhonecall.

List of dependent objects:

-   \[Stage.uspLoadCRMdboPhonecall\]\[spStageuspLoadCRMdboPhonecall\]

-   \[Vault.uspLoadCRMdboPhonecall\]\[spVaultuspLoadCRMdboPhonecall\]

  -----------------------------------------------------------------------------------------------------------
  Id   Column Name                           Data Type          Allow   Description
                                                                Nulls   
  ---- ------------------------------------- ------------------ ------- -------------------------------------
  1    activityadditionalparams              nvarchar(max)      Yes     Column activityadditionalparams from
                                                                        ScaniaCRMExport.dbo.phonecall

  2    activityid                            uniqueidentifier   Yes     Column activityid from
                                                                        ScaniaCRMExport.dbo.phonecall

  3    activitytypecode                      nvarchar(max)      Yes     Column activitytypecode from
                                                                        ScaniaCRMExport.dbo.phonecall

  4    actualdurationminutes                 int                Yes     Column actualdurationminutes from
                                                                        ScaniaCRMExport.dbo.phonecall

  5    actualend                             datetime           Yes     Column actualend from
                                                                        ScaniaCRMExport.dbo.phonecall

  6    actualstart                           datetime           Yes     Column actualstart from
                                                                        ScaniaCRMExport.dbo.phonecall

  7    category                              nvarchar(1000)     Yes     Column category from
                                                                        ScaniaCRMExport.dbo.phonecall

  8    createdby                             uniqueidentifier   Yes     Column createdby from
                                                                        ScaniaCRMExport.dbo.phonecall

  9    createdby\_entitytype                 nvarchar(512)      Yes     Column createdby\_entitytype from
                                                                        ScaniaCRMExport.dbo.phonecall

  10   createdbyname                         nvarchar(400)      Yes     Column createdbyname from
                                                                        ScaniaCRMExport.dbo.phonecall

  11   createdbyyominame                     nvarchar(400)      Yes     Column createdbyyominame from
                                                                        ScaniaCRMExport.dbo.phonecall

  12   createdon                             datetime           Yes     Column createdon from
                                                                        ScaniaCRMExport.dbo.phonecall

  13   createdonbehalfby                     uniqueidentifier   Yes     Column createdonbehalfby from
                                                                        ScaniaCRMExport.dbo.phonecall

  14   createdonbehalfby\_entitytype         nvarchar(512)      Yes     Column createdonbehalfby\_entitytype
                                                                        from ScaniaCRMExport.dbo.phonecall

  15   createdonbehalfbyname                 nvarchar(400)      Yes     Column createdonbehalfbyname from
                                                                        ScaniaCRMExport.dbo.phonecall

  16   createdonbehalfbyyominame             nvarchar(400)      Yes     Column createdonbehalfbyyominame from
                                                                        ScaniaCRMExport.dbo.phonecall

  17   description                           nvarchar(max)      Yes     Column description from
                                                                        ScaniaCRMExport.dbo.phonecall

  18   directioncode                         bit                Yes     Column directioncode from
                                                                        ScaniaCRMExport.dbo.phonecall

  19   exchangerate                          decimal            Yes     Column exchangerate from
                                                                        ScaniaCRMExport.dbo.phonecall

  20   from                                  uniqueidentifier   Yes     Column from from
                                                                        ScaniaCRMExport.dbo.phonecall

  21   Id                                    uniqueidentifier   Yes     Column Id from
                                                                        ScaniaCRMExport.dbo.phonecall

  22   importsequencenumber                  int                Yes     Column importsequencenumber from
                                                                        ScaniaCRMExport.dbo.phonecall

  23   isbilled                              bit                Yes     Column isbilled from
                                                                        ScaniaCRMExport.dbo.phonecall

  24   isregularactivity                     bit                Yes     Column isregularactivity from
                                                                        ScaniaCRMExport.dbo.phonecall

  25   isworkflowcreated                     bit                Yes     Column isworkflowcreated from
                                                                        ScaniaCRMExport.dbo.phonecall

  26   lastonholdtime                        datetime           Yes     Column lastonholdtime from
                                                                        ScaniaCRMExport.dbo.phonecall

  27   leftvoicemail                         bit                Yes     Column leftvoicemail from
                                                                        ScaniaCRMExport.dbo.phonecall

  28   llp\_reportingaccountid               uniqueidentifier   Yes     Column llp\_reportingaccountid from
                                                                        ScaniaCRMExport.dbo.phonecall

  29   llp\_reportingaccountid\_entitytype   nvarchar(512)      Yes     Column
                                                                        llp\_reportingaccountid\_entitytype
                                                                        from ScaniaCRMExport.dbo.phonecall

  30   llp\_reportingaccountidname           nvarchar(640)      Yes     Column llp\_reportingaccountidname
                                                                        from ScaniaCRMExport.dbo.phonecall

  31   llp\_reportingaccountidyominame       nvarchar(640)      Yes     Column
                                                                        llp\_reportingaccountidyominame from
                                                                        ScaniaCRMExport.dbo.phonecall

  32   modifiedby                            uniqueidentifier   Yes     Column modifiedby from
                                                                        ScaniaCRMExport.dbo.phonecall

  33   modifiedby\_entitytype                nvarchar(512)      Yes     Column modifiedby\_entitytype from
                                                                        ScaniaCRMExport.dbo.phonecall

  34   modifiedbyname                        nvarchar(400)      Yes     Column modifiedbyname from
                                                                        ScaniaCRMExport.dbo.phonecall

  35   modifiedbyyominame                    nvarchar(400)      Yes     Column modifiedbyyominame from
                                                                        ScaniaCRMExport.dbo.phonecall

  36   modifiedon                            datetime           Yes     Column modifiedon from
                                                                        ScaniaCRMExport.dbo.phonecall

  37   modifiedonbehalfby                    uniqueidentifier   Yes     Column modifiedonbehalfby from
                                                                        ScaniaCRMExport.dbo.phonecall

  38   modifiedonbehalfby\_entitytype        nvarchar(512)      Yes     Column modifiedonbehalfby\_entitytype
                                                                        from ScaniaCRMExport.dbo.phonecall

  39   modifiedonbehalfbyname                nvarchar(400)      Yes     Column modifiedonbehalfbyname from
                                                                        ScaniaCRMExport.dbo.phonecall

  40   modifiedonbehalfbyyominame            nvarchar(400)      Yes     Column modifiedonbehalfbyyominame
                                                                        from ScaniaCRMExport.dbo.phonecall

  41   onholdtime                            int                Yes     Column onholdtime from
                                                                        ScaniaCRMExport.dbo.phonecall

  42   overriddencreatedon                   datetime           Yes     Column overriddencreatedon from
                                                                        ScaniaCRMExport.dbo.phonecall

  43   ownerid                               uniqueidentifier   Yes     Column ownerid from
                                                                        ScaniaCRMExport.dbo.phonecall

  44   ownerid\_entitytype                   nvarchar(512)      Yes     Column ownerid\_entitytype from
                                                                        ScaniaCRMExport.dbo.phonecall

  45   owneridname                           nvarchar(400)      Yes     Column owneridname from
                                                                        ScaniaCRMExport.dbo.phonecall

  46   owneridtype                           nvarchar(max)      Yes     Column owneridtype from
                                                                        ScaniaCRMExport.dbo.phonecall

  47   owneridyominame                       nvarchar(400)      Yes     Column owneridyominame from
                                                                        ScaniaCRMExport.dbo.phonecall

  48   owningbusinessunit                    uniqueidentifier   Yes     Column owningbusinessunit from
                                                                        ScaniaCRMExport.dbo.phonecall

  49   owningbusinessunit\_entitytype        nvarchar(512)      Yes     Column owningbusinessunit\_entitytype
                                                                        from ScaniaCRMExport.dbo.phonecall

  50   owningteam                            uniqueidentifier   Yes     Column owningteam from
                                                                        ScaniaCRMExport.dbo.phonecall

  51   owningteam\_entitytype                nvarchar(512)      Yes     Column owningteam\_entitytype from
                                                                        ScaniaCRMExport.dbo.phonecall

  52   owninguser                            uniqueidentifier   Yes     Column owninguser from
                                                                        ScaniaCRMExport.dbo.phonecall

  53   owninguser\_entitytype                nvarchar(512)      Yes     Column owninguser\_entitytype from
                                                                        ScaniaCRMExport.dbo.phonecall

  54   phonenumber                           nvarchar(800)      Yes     Column phonenumber from
                                                                        ScaniaCRMExport.dbo.phonecall

  55   prioritycode                          int                Yes     Column prioritycode from
                                                                        ScaniaCRMExport.dbo.phonecall

  56   processid                             uniqueidentifier   Yes     Column processid from
                                                                        ScaniaCRMExport.dbo.phonecall

  57   regardingobjectid                     uniqueidentifier   Yes     Column regardingobjectid from
                                                                        ScaniaCRMExport.dbo.phonecall

  58   regardingobjectid\_entitytype         nvarchar(512)      Yes     Column regardingobjectid\_entitytype
                                                                        from ScaniaCRMExport.dbo.phonecall

  59   regardingobjectidname                 nvarchar(400)      Yes     Column regardingobjectidname from
                                                                        ScaniaCRMExport.dbo.phonecall

  60   regardingobjectidyominame             nvarchar(400)      Yes     Column regardingobjectidyominame from
                                                                        ScaniaCRMExport.dbo.phonecall

  61   regardingobjecttypecode               nvarchar(max)      Yes     Column regardingobjecttypecode from
                                                                        ScaniaCRMExport.dbo.phonecall

  62   scheduleddurationminutes              int                Yes     Column scheduleddurationminutes from
                                                                        ScaniaCRMExport.dbo.phonecall

  63   scheduledend                          datetime           Yes     Column scheduledend from
                                                                        ScaniaCRMExport.dbo.phonecall

  64   scheduledstart                        datetime           Yes     Column scheduledstart from
                                                                        ScaniaCRMExport.dbo.phonecall

  65   serviceid                             uniqueidentifier   Yes     Column serviceid from
                                                                        ScaniaCRMExport.dbo.phonecall

  66   serviceid\_entitytype                 nvarchar(512)      Yes     Column serviceid\_entitytype from
                                                                        ScaniaCRMExport.dbo.phonecall

  67   SinkCreatedOn                         datetime           Yes     Column SinkCreatedOn from
                                                                        ScaniaCRMExport.dbo.phonecall

  68   SinkModifiedOn                        datetime           Yes     Column SinkModifiedOn from
                                                                        ScaniaCRMExport.dbo.phonecall

  69   slaid                                 uniqueidentifier   Yes     Column slaid from
                                                                        ScaniaCRMExport.dbo.phonecall

  70   slaid\_entitytype                     nvarchar(512)      Yes     Column slaid\_entitytype from
                                                                        ScaniaCRMExport.dbo.phonecall

  71   slainvokedid                          uniqueidentifier   Yes     Column slainvokedid from
                                                                        ScaniaCRMExport.dbo.phonecall

  72   slainvokedid\_entitytype              nvarchar(512)      Yes     Column slainvokedid\_entitytype from
                                                                        ScaniaCRMExport.dbo.phonecall

  73   slainvokedidname                      nvarchar(400)      Yes     Column slainvokedidname from
                                                                        ScaniaCRMExport.dbo.phonecall

  74   slaname                               nvarchar(400)      Yes     Column slaname from
                                                                        ScaniaCRMExport.dbo.phonecall

  75   sortdate                              datetime           Yes     Column sortdate from
                                                                        ScaniaCRMExport.dbo.phonecall

  76   stageid                               uniqueidentifier   Yes     Column stageid from
                                                                        ScaniaCRMExport.dbo.phonecall

  77   statecode                             int                Yes     Column statecode from
                                                                        ScaniaCRMExport.dbo.phonecall

  78   statuscode                            int                Yes     Column statuscode from
                                                                        ScaniaCRMExport.dbo.phonecall

  79   subcategory                           nvarchar(1000)     Yes     Column subcategory from
                                                                        ScaniaCRMExport.dbo.phonecall

  80   subject                               nvarchar(800)      Yes     Column subject from
                                                                        ScaniaCRMExport.dbo.phonecall

  81   subscriptionid                        uniqueidentifier   Yes     Column subscriptionid from
                                                                        ScaniaCRMExport.dbo.phonecall

  82   timezoneruleversionnumber             int                Yes     Column timezoneruleversionnumber from
                                                                        ScaniaCRMExport.dbo.phonecall

  83   to                                    uniqueidentifier   Yes     Column to from
                                                                        ScaniaCRMExport.dbo.phonecall

  84   transactioncurrencyid                 uniqueidentifier   Yes     Column transactioncurrencyid from
                                                                        ScaniaCRMExport.dbo.phonecall

  85   transactioncurrencyid\_entitytype     nvarchar(512)      Yes     Column
                                                                        transactioncurrencyid\_entitytype
                                                                        from ScaniaCRMExport.dbo.phonecall

  86   transactioncurrencyidname             nvarchar(400)      Yes     Column transactioncurrencyidname from
                                                                        ScaniaCRMExport.dbo.phonecall

  87   traversedpath                         nvarchar(max)      Yes     Column traversedpath from
                                                                        ScaniaCRMExport.dbo.phonecall

  88   utcconversiontimezonecode             int                Yes     Column utcconversiontimezonecode from
                                                                        ScaniaCRMExport.dbo.phonecall

  89   versionnumber                         bigint             Yes     Column versionnumber from
                                                                        ScaniaCRMExport.dbo.phonecall

  90   DataSourceId                          int                Yes     Id of the data source the row comes
                                                                        from

  91   ThreadLogId                           int                Yes     Id of ThreadLog which inserted the
                                                                        row
  -----------------------------------------------------------------------------------------------------------

\[Back to table list\]\[listoftables\]
