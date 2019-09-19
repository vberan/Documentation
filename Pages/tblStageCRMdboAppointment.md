Table Stage.CRMdboAppointment {#tblStageCRMdboAppointment}
-----------------------------

Description:

Stage table CRMdboAppointment.

List of dependent objects:

-   \[Stage.uspLoadCRMdboAppointment\]\[spStageuspLoadCRMdboAppointment\]

-   \[Vault.uspLoadCRMdboAppointment\]\[spVaultuspLoadCRMdboAppointment\]

  ------------------------------------------------------------------------------------------------------------
  Id    Column Name                           Data Type          Allow   Description
                                                                 Nulls   
  ----- ------------------------------------- ------------------ ------- -------------------------------------
  1     activityadditionalparams              nvarchar(max)      Yes     Column activityadditionalparams from
                                                                         ScaniaCRMExport.dbo.appointment

  2     activityid                            uniqueidentifier   Yes     Column activityid from
                                                                         ScaniaCRMExport.dbo.appointment

  3     activitytypecode                      nvarchar(max)      Yes     Column activitytypecode from
                                                                         ScaniaCRMExport.dbo.appointment

  4     actualdurationminutes                 int                Yes     Column actualdurationminutes from
                                                                         ScaniaCRMExport.dbo.appointment

  5     actualend                             datetime           Yes     Column actualend from
                                                                         ScaniaCRMExport.dbo.appointment

  6     actualstart                           datetime           Yes     Column actualstart from
                                                                         ScaniaCRMExport.dbo.appointment

  7     attachmentcount                       int                Yes     Column attachmentcount from
                                                                         ScaniaCRMExport.dbo.appointment

  8     attachmenterrors                      int                Yes     Column attachmenterrors from
                                                                         ScaniaCRMExport.dbo.appointment

  9     category                              nvarchar(1000)     Yes     Column category from
                                                                         ScaniaCRMExport.dbo.appointment

  10    createdby                             uniqueidentifier   Yes     Column createdby from
                                                                         ScaniaCRMExport.dbo.appointment

  11    createdby\_entitytype                 nvarchar(512)      Yes     Column createdby\_entitytype from
                                                                         ScaniaCRMExport.dbo.appointment

  12    createdbyname                         nvarchar(400)      Yes     Column createdbyname from
                                                                         ScaniaCRMExport.dbo.appointment

  13    createdbyyominame                     nvarchar(400)      Yes     Column createdbyyominame from
                                                                         ScaniaCRMExport.dbo.appointment

  14    createdon                             datetime           Yes     Column createdon from
                                                                         ScaniaCRMExport.dbo.appointment

  15    createdonbehalfby                     uniqueidentifier   Yes     Column createdonbehalfby from
                                                                         ScaniaCRMExport.dbo.appointment

  16    createdonbehalfby\_entitytype         nvarchar(512)      Yes     Column createdonbehalfby\_entitytype
                                                                         from ScaniaCRMExport.dbo.appointment

  17    createdonbehalfbyname                 nvarchar(400)      Yes     Column createdonbehalfbyname from
                                                                         ScaniaCRMExport.dbo.appointment

  18    createdonbehalfbyyominame             nvarchar(400)      Yes     Column createdonbehalfbyyominame from
                                                                         ScaniaCRMExport.dbo.appointment

  19    description                           nvarchar(max)      Yes     Column description from
                                                                         ScaniaCRMExport.dbo.appointment

  20    exchangerate                          decimal            Yes     Column exchangerate from
                                                                         ScaniaCRMExport.dbo.appointment

  21    globalobjectid                        nvarchar(1200)     Yes     Column globalobjectid from
                                                                         ScaniaCRMExport.dbo.appointment

  22    Id                                    uniqueidentifier   Yes     Column Id from
                                                                         ScaniaCRMExport.dbo.appointment

  23    importsequencenumber                  int                Yes     Column importsequencenumber from
                                                                         ScaniaCRMExport.dbo.appointment

  24    instancetypecode                      int                Yes     Column instancetypecode from
                                                                         ScaniaCRMExport.dbo.appointment

  25    isalldayevent                         bit                Yes     Column isalldayevent from
                                                                         ScaniaCRMExport.dbo.appointment

  26    isbilled                              bit                Yes     Column isbilled from
                                                                         ScaniaCRMExport.dbo.appointment

  27    isdraft                               bit                Yes     Column isdraft from
                                                                         ScaniaCRMExport.dbo.appointment

  28    ismapiprivate                         bit                Yes     Column ismapiprivate from
                                                                         ScaniaCRMExport.dbo.appointment

  29    isregularactivity                     bit                Yes     Column isregularactivity from
                                                                         ScaniaCRMExport.dbo.appointment

  30    isunsafe                              int                Yes     Column isunsafe from
                                                                         ScaniaCRMExport.dbo.appointment

  31    isworkflowcreated                     bit                Yes     Column isworkflowcreated from
                                                                         ScaniaCRMExport.dbo.appointment

  32    lastonholdtime                        datetime           Yes     Column lastonholdtime from
                                                                         ScaniaCRMExport.dbo.appointment

  33    llp\_importbatch                      nvarchar(400)      Yes     Column llp\_importbatch from
                                                                         ScaniaCRMExport.dbo.appointment

  34    llp\_reportingaccountid               uniqueidentifier   Yes     Column llp\_reportingaccountid from
                                                                         ScaniaCRMExport.dbo.appointment

  35    llp\_reportingaccountid\_entitytype   nvarchar(512)      Yes     Column
                                                                         llp\_reportingaccountid\_entitytype
                                                                         from ScaniaCRMExport.dbo.appointment

  36    llp\_reportingaccountidname           nvarchar(640)      Yes     Column llp\_reportingaccountidname
                                                                         from ScaniaCRMExport.dbo.appointment

  37    llp\_reportingaccountidyominame       nvarchar(640)      Yes     Column
                                                                         llp\_reportingaccountidyominame from
                                                                         ScaniaCRMExport.dbo.appointment

  38    location                              nvarchar(800)      Yes     Column location from
                                                                         ScaniaCRMExport.dbo.appointment

  39    modifiedby                            uniqueidentifier   Yes     Column modifiedby from
                                                                         ScaniaCRMExport.dbo.appointment

  40    modifiedby\_entitytype                nvarchar(512)      Yes     Column modifiedby\_entitytype from
                                                                         ScaniaCRMExport.dbo.appointment

  41    modifiedbyname                        nvarchar(400)      Yes     Column modifiedbyname from
                                                                         ScaniaCRMExport.dbo.appointment

  42    modifiedbyyominame                    nvarchar(400)      Yes     Column modifiedbyyominame from
                                                                         ScaniaCRMExport.dbo.appointment

  43    modifiedfieldsmask                    nvarchar(max)      Yes     Column modifiedfieldsmask from
                                                                         ScaniaCRMExport.dbo.appointment

  44    modifiedon                            datetime           Yes     Column modifiedon from
                                                                         ScaniaCRMExport.dbo.appointment

  45    modifiedonbehalfby                    uniqueidentifier   Yes     Column modifiedonbehalfby from
                                                                         ScaniaCRMExport.dbo.appointment

  46    modifiedonbehalfby\_entitytype        nvarchar(512)      Yes     Column modifiedonbehalfby\_entitytype
                                                                         from ScaniaCRMExport.dbo.appointment

  47    modifiedonbehalfbyname                nvarchar(400)      Yes     Column modifiedonbehalfbyname from
                                                                         ScaniaCRMExport.dbo.appointment

  48    modifiedonbehalfbyyominame            nvarchar(400)      Yes     Column modifiedonbehalfbyyominame
                                                                         from ScaniaCRMExport.dbo.appointment

  49    onholdtime                            int                Yes     Column onholdtime from
                                                                         ScaniaCRMExport.dbo.appointment

  50    optionalattendees                     uniqueidentifier   Yes     Column optionalattendees from
                                                                         ScaniaCRMExport.dbo.appointment

  51    organizer                             uniqueidentifier   Yes     Column organizer from
                                                                         ScaniaCRMExport.dbo.appointment

  52    originalstartdate                     datetime           Yes     Column originalstartdate from
                                                                         ScaniaCRMExport.dbo.appointment

  53    outlookownerapptid                    int                Yes     Column outlookownerapptid from
                                                                         ScaniaCRMExport.dbo.appointment

  54    overriddencreatedon                   datetime           Yes     Column overriddencreatedon from
                                                                         ScaniaCRMExport.dbo.appointment

  55    ownerid                               uniqueidentifier   Yes     Column ownerid from
                                                                         ScaniaCRMExport.dbo.appointment

  56    ownerid\_entitytype                   nvarchar(512)      Yes     Column ownerid\_entitytype from
                                                                         ScaniaCRMExport.dbo.appointment

  57    owneridname                           nvarchar(400)      Yes     Column owneridname from
                                                                         ScaniaCRMExport.dbo.appointment

  58    owneridtype                           nvarchar(max)      Yes     Column owneridtype from
                                                                         ScaniaCRMExport.dbo.appointment

  59    owneridyominame                       nvarchar(400)      Yes     Column owneridyominame from
                                                                         ScaniaCRMExport.dbo.appointment

  60    owningbusinessunit                    uniqueidentifier   Yes     Column owningbusinessunit from
                                                                         ScaniaCRMExport.dbo.appointment

  61    owningbusinessunit\_entitytype        nvarchar(512)      Yes     Column owningbusinessunit\_entitytype
                                                                         from ScaniaCRMExport.dbo.appointment

  62    owningteam                            uniqueidentifier   Yes     Column owningteam from
                                                                         ScaniaCRMExport.dbo.appointment

  63    owningteam\_entitytype                nvarchar(512)      Yes     Column owningteam\_entitytype from
                                                                         ScaniaCRMExport.dbo.appointment

  64    owninguser                            uniqueidentifier   Yes     Column owninguser from
                                                                         ScaniaCRMExport.dbo.appointment

  65    owninguser\_entitytype                nvarchar(512)      Yes     Column owninguser\_entitytype from
                                                                         ScaniaCRMExport.dbo.appointment

  66    prioritycode                          int                Yes     Column prioritycode from
                                                                         ScaniaCRMExport.dbo.appointment

  67    processid                             uniqueidentifier   Yes     Column processid from
                                                                         ScaniaCRMExport.dbo.appointment

  68    regardingobjectid                     uniqueidentifier   Yes     Column regardingobjectid from
                                                                         ScaniaCRMExport.dbo.appointment

  69    regardingobjectid\_entitytype         nvarchar(512)      Yes     Column regardingobjectid\_entitytype
                                                                         from ScaniaCRMExport.dbo.appointment

  70    regardingobjectidname                 nvarchar(400)      Yes     Column regardingobjectidname from
                                                                         ScaniaCRMExport.dbo.appointment

  71    regardingobjectidyominame             nvarchar(400)      Yes     Column regardingobjectidyominame from
                                                                         ScaniaCRMExport.dbo.appointment

  72    regardingobjecttypecode               nvarchar(max)      Yes     Column regardingobjecttypecode from
                                                                         ScaniaCRMExport.dbo.appointment

  73    requiredattendees                     uniqueidentifier   Yes     Column requiredattendees from
                                                                         ScaniaCRMExport.dbo.appointment

  74    resco\_eventid                        nvarchar(800)      Yes     Column resco\_eventid from
                                                                         ScaniaCRMExport.dbo.appointment

  75    resco\_externalid                     nvarchar(800)      Yes     Column resco\_externalid from
                                                                         ScaniaCRMExport.dbo.appointment

  76    resco\_islocal                        bit                Yes     Column resco\_islocal from
                                                                         ScaniaCRMExport.dbo.appointment

  77    resco\_source                         int                Yes     Column resco\_source from
                                                                         ScaniaCRMExport.dbo.appointment

  78    safedescription                       nvarchar(max)      Yes     Column safedescription from
                                                                         ScaniaCRMExport.dbo.appointment

  79    scheduleddurationminutes              int                Yes     Column scheduleddurationminutes from
                                                                         ScaniaCRMExport.dbo.appointment

  80    scheduledend                          datetime           Yes     Column scheduledend from
                                                                         ScaniaCRMExport.dbo.appointment

  81    scheduledstart                        datetime           Yes     Column scheduledstart from
                                                                         ScaniaCRMExport.dbo.appointment

  82    seriesid                              uniqueidentifier   Yes     Column seriesid from
                                                                         ScaniaCRMExport.dbo.appointment

  83    serviceid                             uniqueidentifier   Yes     Column serviceid from
                                                                         ScaniaCRMExport.dbo.appointment

  84    serviceid\_entitytype                 nvarchar(512)      Yes     Column serviceid\_entitytype from
                                                                         ScaniaCRMExport.dbo.appointment

  85    SinkCreatedOn                         datetime           Yes     Column SinkCreatedOn from
                                                                         ScaniaCRMExport.dbo.appointment

  86    SinkModifiedOn                        datetime           Yes     Column SinkModifiedOn from
                                                                         ScaniaCRMExport.dbo.appointment

  87    slaid                                 uniqueidentifier   Yes     Column slaid from
                                                                         ScaniaCRMExport.dbo.appointment

  88    slaid\_entitytype                     nvarchar(512)      Yes     Column slaid\_entitytype from
                                                                         ScaniaCRMExport.dbo.appointment

  89    slainvokedid                          uniqueidentifier   Yes     Column slainvokedid from
                                                                         ScaniaCRMExport.dbo.appointment

  90    slainvokedid\_entitytype              nvarchar(512)      Yes     Column slainvokedid\_entitytype from
                                                                         ScaniaCRMExport.dbo.appointment

  91    slainvokedidname                      nvarchar(400)      Yes     Column slainvokedidname from
                                                                         ScaniaCRMExport.dbo.appointment

  92    slaname                               nvarchar(400)      Yes     Column slaname from
                                                                         ScaniaCRMExport.dbo.appointment

  93    sortdate                              datetime           Yes     Column sortdate from
                                                                         ScaniaCRMExport.dbo.appointment

  94    stageid                               uniqueidentifier   Yes     Column stageid from
                                                                         ScaniaCRMExport.dbo.appointment

  95    statecode                             int                Yes     Column statecode from
                                                                         ScaniaCRMExport.dbo.appointment

  96    statuscode                            int                Yes     Column statuscode from
                                                                         ScaniaCRMExport.dbo.appointment

  97    subcategory                           nvarchar(1000)     Yes     Column subcategory from
                                                                         ScaniaCRMExport.dbo.appointment

  98    subject                               nvarchar(800)      Yes     Column subject from
                                                                         ScaniaCRMExport.dbo.appointment

  99    subscriptionid                        uniqueidentifier   Yes     Column subscriptionid from
                                                                         ScaniaCRMExport.dbo.appointment

  100   timezoneruleversionnumber             int                Yes     Column timezoneruleversionnumber from
                                                                         ScaniaCRMExport.dbo.appointment

  101   transactioncurrencyid                 uniqueidentifier   Yes     Column transactioncurrencyid from
                                                                         ScaniaCRMExport.dbo.appointment

  102   transactioncurrencyid\_entitytype     nvarchar(512)      Yes     Column
                                                                         transactioncurrencyid\_entitytype
                                                                         from ScaniaCRMExport.dbo.appointment

  103   transactioncurrencyidname             nvarchar(400)      Yes     Column transactioncurrencyidname from
                                                                         ScaniaCRMExport.dbo.appointment

  104   traversedpath                         nvarchar(max)      Yes     Column traversedpath from
                                                                         ScaniaCRMExport.dbo.appointment

  105   utcconversiontimezonecode             int                Yes     Column utcconversiontimezonecode from
                                                                         ScaniaCRMExport.dbo.appointment

  106   versionnumber                         bigint             Yes     Column versionnumber from
                                                                         ScaniaCRMExport.dbo.appointment

  107   DataSourceId                          int                Yes     Id of the data source the row comes
                                                                         from

  108   ThreadLogId                           int                Yes     Id of ThreadLog which inserted the
                                                                         row
  ------------------------------------------------------------------------------------------------------------

\[Back to table list\]\[listoftables\]
