Table Stage.CRMdboEmail {#tblStageCRMdboEmail}
-----------------------

Description:

Stage table CRMdboEmail.

List of dependent objects:

-   \[Stage.uspLoadCRMdboEmail\]\[spStageuspLoadCRMdboEmail\]

-   \[Vault.uspLoadCRMdboEmail\]\[spVaultuspLoadCRMdboEmail\]

  ------------------------------------------------------------------------------------------------------------
  Id    Column Name                           Data Type          Allow   Description
                                                                 Nulls   
  ----- ------------------------------------- ------------------ ------- -------------------------------------
  1     activityadditionalparams              nvarchar(max)      Yes     Column activityadditionalparams from
                                                                         ScaniaCRMExport.dbo.email

  2     activityid                            uniqueidentifier   Yes     Column activityid from
                                                                         ScaniaCRMExport.dbo.email

  3     activitytypecode                      nvarchar(max)      Yes     Column activitytypecode from
                                                                         ScaniaCRMExport.dbo.email

  4     actualdurationminutes                 int                Yes     Column actualdurationminutes from
                                                                         ScaniaCRMExport.dbo.email

  5     actualend                             datetime           Yes     Column actualend from
                                                                         ScaniaCRMExport.dbo.email

  6     actualstart                           datetime           Yes     Column actualstart from
                                                                         ScaniaCRMExport.dbo.email

  7     attachmentcount                       int                Yes     Column attachmentcount from
                                                                         ScaniaCRMExport.dbo.email

  8     attachmentopencount                   int                Yes     Column attachmentopencount from
                                                                         ScaniaCRMExport.dbo.email

  9     baseconversationindexhash             int                Yes     Column baseconversationindexhash from
                                                                         ScaniaCRMExport.dbo.email

  10    bcc                                   uniqueidentifier   Yes     Column bcc from
                                                                         ScaniaCRMExport.dbo.email

  11    category                              nvarchar(1000)     Yes     Column category from
                                                                         ScaniaCRMExport.dbo.email

  12    cc                                    uniqueidentifier   Yes     Column cc from
                                                                         ScaniaCRMExport.dbo.email

  13    compressed                            bit                Yes     Column compressed from
                                                                         ScaniaCRMExport.dbo.email

  14    conversationindex                     nvarchar(max)      Yes     Column conversationindex from
                                                                         ScaniaCRMExport.dbo.email

  15    conversationtrackingid                uniqueidentifier   Yes     Column conversationtrackingid from
                                                                         ScaniaCRMExport.dbo.email

  16    correlationmethod                     int                Yes     Column correlationmethod from
                                                                         ScaniaCRMExport.dbo.email

  17    createdby                             uniqueidentifier   Yes     Column createdby from
                                                                         ScaniaCRMExport.dbo.email

  18    createdby\_entitytype                 nvarchar(512)      Yes     Column createdby\_entitytype from
                                                                         ScaniaCRMExport.dbo.email

  19    createdbyname                         nvarchar(400)      Yes     Column createdbyname from
                                                                         ScaniaCRMExport.dbo.email

  20    createdbyyominame                     nvarchar(400)      Yes     Column createdbyyominame from
                                                                         ScaniaCRMExport.dbo.email

  21    createdon                             datetime           Yes     Column createdon from
                                                                         ScaniaCRMExport.dbo.email

  22    createdonbehalfby                     uniqueidentifier   Yes     Column createdonbehalfby from
                                                                         ScaniaCRMExport.dbo.email

  23    createdonbehalfby\_entitytype         nvarchar(512)      Yes     Column createdonbehalfby\_entitytype
                                                                         from ScaniaCRMExport.dbo.email

  24    createdonbehalfbyname                 nvarchar(400)      Yes     Column createdonbehalfbyname from
                                                                         ScaniaCRMExport.dbo.email

  25    createdonbehalfbyyominame             nvarchar(400)      Yes     Column createdonbehalfbyyominame from
                                                                         ScaniaCRMExport.dbo.email

  26    delayedemailsendtime                  datetime           Yes     Column delayedemailsendtime from
                                                                         ScaniaCRMExport.dbo.email

  27    deliveryattempts                      int                Yes     Column deliveryattempts from
                                                                         ScaniaCRMExport.dbo.email

  28    deliveryprioritycode                  int                Yes     Column deliveryprioritycode from
                                                                         ScaniaCRMExport.dbo.email

  29    deliveryreceiptrequested              bit                Yes     Column deliveryreceiptrequested from
                                                                         ScaniaCRMExport.dbo.email

  30    description                           nvarchar(max)      Yes     Column description from
                                                                         ScaniaCRMExport.dbo.email

  31    directioncode                         bit                Yes     Column directioncode from
                                                                         ScaniaCRMExport.dbo.email

  32    emailreminderexpirytime               datetime           Yes     Column emailreminderexpirytime from
                                                                         ScaniaCRMExport.dbo.email

  33    emailreminderstatus                   int                Yes     Column emailreminderstatus from
                                                                         ScaniaCRMExport.dbo.email

  34    emailremindertext                     nvarchar(max)      Yes     Column emailremindertext from
                                                                         ScaniaCRMExport.dbo.email

  35    emailremindertype                     int                Yes     Column emailremindertype from
                                                                         ScaniaCRMExport.dbo.email

  36    emailsender                           uniqueidentifier   Yes     Column emailsender from
                                                                         ScaniaCRMExport.dbo.email

  37    emailsender\_entitytype               nvarchar(512)      Yes     Column emailsender\_entitytype from
                                                                         ScaniaCRMExport.dbo.email

  38    emailsendername                       nvarchar(1600)     Yes     Column emailsendername from
                                                                         ScaniaCRMExport.dbo.email

  39    emailsenderobjecttypecode             nvarchar(max)      Yes     Column emailsenderobjecttypecode from
                                                                         ScaniaCRMExport.dbo.email

  40    emailsenderyominame                   nvarchar(1600)     Yes     Column emailsenderyominame from
                                                                         ScaniaCRMExport.dbo.email

  41    emailtrackingid                       uniqueidentifier   Yes     Column emailtrackingid from
                                                                         ScaniaCRMExport.dbo.email

  42    exchangerate                          decimal            Yes     Column exchangerate from
                                                                         ScaniaCRMExport.dbo.email

  43    followemailuserpreference             bit                Yes     Column followemailuserpreference from
                                                                         ScaniaCRMExport.dbo.email

  44    from                                  uniqueidentifier   Yes     Column from from
                                                                         ScaniaCRMExport.dbo.email

  45    Id                                    uniqueidentifier   Yes     Column Id from
                                                                         ScaniaCRMExport.dbo.email

  46    importsequencenumber                  int                Yes     Column importsequencenumber from
                                                                         ScaniaCRMExport.dbo.email

  47    inreplyto                             nvarchar(1280)     Yes     Column inreplyto from
                                                                         ScaniaCRMExport.dbo.email

  48    isbilled                              bit                Yes     Column isbilled from
                                                                         ScaniaCRMExport.dbo.email

  49    isemailfollowed                       bit                Yes     Column isemailfollowed from
                                                                         ScaniaCRMExport.dbo.email

  50    isemailreminderset                    bit                Yes     Column isemailreminderset from
                                                                         ScaniaCRMExport.dbo.email

  51    isregularactivity                     bit                Yes     Column isregularactivity from
                                                                         ScaniaCRMExport.dbo.email

  52    isunsafe                              int                Yes     Column isunsafe from
                                                                         ScaniaCRMExport.dbo.email

  53    isworkflowcreated                     bit                Yes     Column isworkflowcreated from
                                                                         ScaniaCRMExport.dbo.email

  54    lastonholdtime                        datetime           Yes     Column lastonholdtime from
                                                                         ScaniaCRMExport.dbo.email

  55    lastopenedtime                        datetime           Yes     Column lastopenedtime from
                                                                         ScaniaCRMExport.dbo.email

  56    linksclickedcount                     int                Yes     Column linksclickedcount from
                                                                         ScaniaCRMExport.dbo.email

  57    llp\_reportingaccountid               uniqueidentifier   Yes     Column llp\_reportingaccountid from
                                                                         ScaniaCRMExport.dbo.email

  58    llp\_reportingaccountid\_entitytype   nvarchar(512)      Yes     Column
                                                                         llp\_reportingaccountid\_entitytype
                                                                         from ScaniaCRMExport.dbo.email

  59    llp\_reportingaccountidname           nvarchar(640)      Yes     Column llp\_reportingaccountidname
                                                                         from ScaniaCRMExport.dbo.email

  60    llp\_reportingaccountidyominame       nvarchar(640)      Yes     Column
                                                                         llp\_reportingaccountidyominame from
                                                                         ScaniaCRMExport.dbo.email

  61    messageid                             nvarchar(1280)     Yes     Column messageid from
                                                                         ScaniaCRMExport.dbo.email

  62    messageiddupcheck                     uniqueidentifier   Yes     Column messageiddupcheck from
                                                                         ScaniaCRMExport.dbo.email

  63    mimetype                              nvarchar(1024)     Yes     Column mimetype from
                                                                         ScaniaCRMExport.dbo.email

  64    modifiedby                            uniqueidentifier   Yes     Column modifiedby from
                                                                         ScaniaCRMExport.dbo.email

  65    modifiedby\_entitytype                nvarchar(512)      Yes     Column modifiedby\_entitytype from
                                                                         ScaniaCRMExport.dbo.email

  66    modifiedbyname                        nvarchar(400)      Yes     Column modifiedbyname from
                                                                         ScaniaCRMExport.dbo.email

  67    modifiedbyyominame                    nvarchar(400)      Yes     Column modifiedbyyominame from
                                                                         ScaniaCRMExport.dbo.email

  68    modifiedon                            datetime           Yes     Column modifiedon from
                                                                         ScaniaCRMExport.dbo.email

  69    modifiedonbehalfby                    uniqueidentifier   Yes     Column modifiedonbehalfby from
                                                                         ScaniaCRMExport.dbo.email

  70    modifiedonbehalfby\_entitytype        nvarchar(512)      Yes     Column modifiedonbehalfby\_entitytype
                                                                         from ScaniaCRMExport.dbo.email

  71    modifiedonbehalfbyname                nvarchar(400)      Yes     Column modifiedonbehalfbyname from
                                                                         ScaniaCRMExport.dbo.email

  72    modifiedonbehalfbyyominame            nvarchar(400)      Yes     Column modifiedonbehalfbyyominame
                                                                         from ScaniaCRMExport.dbo.email

  73    notifications                         int                Yes     Column notifications from
                                                                         ScaniaCRMExport.dbo.email

  74    onholdtime                            int                Yes     Column onholdtime from
                                                                         ScaniaCRMExport.dbo.email

  75    opencount                             int                Yes     Column opencount from
                                                                         ScaniaCRMExport.dbo.email

  76    overriddencreatedon                   datetime           Yes     Column overriddencreatedon from
                                                                         ScaniaCRMExport.dbo.email

  77    ownerid                               uniqueidentifier   Yes     Column ownerid from
                                                                         ScaniaCRMExport.dbo.email

  78    ownerid\_entitytype                   nvarchar(512)      Yes     Column ownerid\_entitytype from
                                                                         ScaniaCRMExport.dbo.email

  79    owneridname                           nvarchar(400)      Yes     Column owneridname from
                                                                         ScaniaCRMExport.dbo.email

  80    owneridtype                           nvarchar(max)      Yes     Column owneridtype from
                                                                         ScaniaCRMExport.dbo.email

  81    owneridyominame                       nvarchar(400)      Yes     Column owneridyominame from
                                                                         ScaniaCRMExport.dbo.email

  82    owningbusinessunit                    uniqueidentifier   Yes     Column owningbusinessunit from
                                                                         ScaniaCRMExport.dbo.email

  83    owningbusinessunit\_entitytype        nvarchar(512)      Yes     Column owningbusinessunit\_entitytype
                                                                         from ScaniaCRMExport.dbo.email

  84    owningteam                            uniqueidentifier   Yes     Column owningteam from
                                                                         ScaniaCRMExport.dbo.email

  85    owningteam\_entitytype                nvarchar(512)      Yes     Column owningteam\_entitytype from
                                                                         ScaniaCRMExport.dbo.email

  86    owninguser                            uniqueidentifier   Yes     Column owninguser from
                                                                         ScaniaCRMExport.dbo.email

  87    owninguser\_entitytype                nvarchar(512)      Yes     Column owninguser\_entitytype from
                                                                         ScaniaCRMExport.dbo.email

  88    parentactivityid                      uniqueidentifier   Yes     Column parentactivityid from
                                                                         ScaniaCRMExport.dbo.email

  89    parentactivityid\_entitytype          nvarchar(512)      Yes     Column parentactivityid\_entitytype
                                                                         from ScaniaCRMExport.dbo.email

  90    parentactivityidname                  nvarchar(1600)     Yes     Column parentactivityidname from
                                                                         ScaniaCRMExport.dbo.email

  91    postponeemailprocessinguntil          datetime           Yes     Column postponeemailprocessinguntil
                                                                         from ScaniaCRMExport.dbo.email

  92    prioritycode                          int                Yes     Column prioritycode from
                                                                         ScaniaCRMExport.dbo.email

  93    processid                             uniqueidentifier   Yes     Column processid from
                                                                         ScaniaCRMExport.dbo.email

  94    readreceiptrequested                  bit                Yes     Column readreceiptrequested from
                                                                         ScaniaCRMExport.dbo.email

  95    regardingobjectid                     uniqueidentifier   Yes     Column regardingobjectid from
                                                                         ScaniaCRMExport.dbo.email

  96    regardingobjectid\_entitytype         nvarchar(512)      Yes     Column regardingobjectid\_entitytype
                                                                         from ScaniaCRMExport.dbo.email

  97    regardingobjectidname                 nvarchar(400)      Yes     Column regardingobjectidname from
                                                                         ScaniaCRMExport.dbo.email

  98    regardingobjectidyominame             nvarchar(400)      Yes     Column regardingobjectidyominame from
                                                                         ScaniaCRMExport.dbo.email

  99    regardingobjecttypecode               nvarchar(max)      Yes     Column regardingobjecttypecode from
                                                                         ScaniaCRMExport.dbo.email

  100   reminderactioncardid                  uniqueidentifier   Yes     Column reminderactioncardid from
                                                                         ScaniaCRMExport.dbo.email

  101   replycount                            int                Yes     Column replycount from
                                                                         ScaniaCRMExport.dbo.email

  102   resco\_contentstatus                  int                Yes     Column resco\_contentstatus from
                                                                         ScaniaCRMExport.dbo.email

  103   resco\_createdas                      int                Yes     Column resco\_createdas from
                                                                         ScaniaCRMExport.dbo.email

  104   resco\_createdfrom                    nvarchar(800)      Yes     Column resco\_createdfrom from
                                                                         ScaniaCRMExport.dbo.email

  105   resco\_emailid                        nvarchar(800)      Yes     Column resco\_emailid from
                                                                         ScaniaCRMExport.dbo.email

  106   resco\_eventid                        nvarchar(800)      Yes     Column resco\_eventid from
                                                                         ScaniaCRMExport.dbo.email

  107   resco\_islocal                        bit                Yes     Column resco\_islocal from
                                                                         ScaniaCRMExport.dbo.email

  108   resco\_snippet                        nvarchar(max)      Yes     Column resco\_snippet from
                                                                         ScaniaCRMExport.dbo.email

  109   resco\_source                         int                Yes     Column resco\_source from
                                                                         ScaniaCRMExport.dbo.email

  110   resco\_statuscode                     int                Yes     Column resco\_statuscode from
                                                                         ScaniaCRMExport.dbo.email

  111   resco\_threadid                       nvarchar(800)      Yes     Column resco\_threadid from
                                                                         ScaniaCRMExport.dbo.email

  112   safedescription                       nvarchar(max)      Yes     Column safedescription from
                                                                         ScaniaCRMExport.dbo.email

  113   scheduleddurationminutes              int                Yes     Column scheduleddurationminutes from
                                                                         ScaniaCRMExport.dbo.email

  114   scheduledend                          datetime           Yes     Column scheduledend from
                                                                         ScaniaCRMExport.dbo.email

  115   scheduledstart                        datetime           Yes     Column scheduledstart from
                                                                         ScaniaCRMExport.dbo.email

  116   sender                                nvarchar(1000)     Yes     Column sender from
                                                                         ScaniaCRMExport.dbo.email

  117   sendermailboxid                       uniqueidentifier   Yes     Column sendermailboxid from
                                                                         ScaniaCRMExport.dbo.email

  118   sendermailboxid\_entitytype           nvarchar(512)      Yes     Column sendermailboxid\_entitytype
                                                                         from ScaniaCRMExport.dbo.email

  119   sendermailboxidname                   nvarchar(400)      Yes     Column sendermailboxidname from
                                                                         ScaniaCRMExport.dbo.email

  120   sendersaccount                        uniqueidentifier   Yes     Column sendersaccount from
                                                                         ScaniaCRMExport.dbo.email

  121   sendersaccount\_entitytype            nvarchar(512)      Yes     Column sendersaccount\_entitytype
                                                                         from ScaniaCRMExport.dbo.email

  122   sendersaccountname                    nvarchar(1600)     Yes     Column sendersaccountname from
                                                                         ScaniaCRMExport.dbo.email

  123   sendersaccountobjecttypecode          nvarchar(max)      Yes     Column sendersaccountobjecttypecode
                                                                         from ScaniaCRMExport.dbo.email

  124   sendersaccountyominame                nvarchar(1600)     Yes     Column sendersaccountyominame from
                                                                         ScaniaCRMExport.dbo.email

  125   senton                                datetime           Yes     Column senton from
                                                                         ScaniaCRMExport.dbo.email

  126   serviceid                             uniqueidentifier   Yes     Column serviceid from
                                                                         ScaniaCRMExport.dbo.email

  127   serviceid\_entitytype                 nvarchar(512)      Yes     Column serviceid\_entitytype from
                                                                         ScaniaCRMExport.dbo.email

  128   SinkCreatedOn                         datetime           Yes     Column SinkCreatedOn from
                                                                         ScaniaCRMExport.dbo.email

  129   SinkModifiedOn                        datetime           Yes     Column SinkModifiedOn from
                                                                         ScaniaCRMExport.dbo.email

  130   slaid                                 uniqueidentifier   Yes     Column slaid from
                                                                         ScaniaCRMExport.dbo.email

  131   slaid\_entitytype                     nvarchar(512)      Yes     Column slaid\_entitytype from
                                                                         ScaniaCRMExport.dbo.email

  132   slainvokedid                          uniqueidentifier   Yes     Column slainvokedid from
                                                                         ScaniaCRMExport.dbo.email

  133   slainvokedid\_entitytype              nvarchar(512)      Yes     Column slainvokedid\_entitytype from
                                                                         ScaniaCRMExport.dbo.email

  134   slainvokedidname                      nvarchar(400)      Yes     Column slainvokedidname from
                                                                         ScaniaCRMExport.dbo.email

  135   slaname                               nvarchar(400)      Yes     Column slaname from
                                                                         ScaniaCRMExport.dbo.email

  136   sortdate                              datetime           Yes     Column sortdate from
                                                                         ScaniaCRMExport.dbo.email

  137   stageid                               uniqueidentifier   Yes     Column stageid from
                                                                         ScaniaCRMExport.dbo.email

  138   statecode                             int                Yes     Column statecode from
                                                                         ScaniaCRMExport.dbo.email

  139   statuscode                            int                Yes     Column statuscode from
                                                                         ScaniaCRMExport.dbo.email

  140   subcategory                           nvarchar(1000)     Yes     Column subcategory from
                                                                         ScaniaCRMExport.dbo.email

  141   subject                               nvarchar(1600)     Yes     Column subject from
                                                                         ScaniaCRMExport.dbo.email

  142   submittedby                           nvarchar(1000)     Yes     Column submittedby from
                                                                         ScaniaCRMExport.dbo.email

  143   templateid                            uniqueidentifier   Yes     Column templateid from
                                                                         ScaniaCRMExport.dbo.email

  144   templateid\_entitytype                nvarchar(512)      Yes     Column templateid\_entitytype from
                                                                         ScaniaCRMExport.dbo.email

  145   templateidname                        nvarchar(400)      Yes     Column templateidname from
                                                                         ScaniaCRMExport.dbo.email

  146   timezoneruleversionnumber             int                Yes     Column timezoneruleversionnumber from
                                                                         ScaniaCRMExport.dbo.email

  147   to                                    uniqueidentifier   Yes     Column to from
                                                                         ScaniaCRMExport.dbo.email

  148   torecipients                          nvarchar(2000)     Yes     Column torecipients from
                                                                         ScaniaCRMExport.dbo.email

  149   trackingtoken                         nvarchar(200)      Yes     Column trackingtoken from
                                                                         ScaniaCRMExport.dbo.email

  150   transactioncurrencyid                 uniqueidentifier   Yes     Column transactioncurrencyid from
                                                                         ScaniaCRMExport.dbo.email

  151   transactioncurrencyid\_entitytype     nvarchar(512)      Yes     Column
                                                                         transactioncurrencyid\_entitytype
                                                                         from ScaniaCRMExport.dbo.email

  152   transactioncurrencyidname             nvarchar(400)      Yes     Column transactioncurrencyidname from
                                                                         ScaniaCRMExport.dbo.email

  153   traversedpath                         nvarchar(max)      Yes     Column traversedpath from
                                                                         ScaniaCRMExport.dbo.email

  154   utcconversiontimezonecode             int                Yes     Column utcconversiontimezonecode from
                                                                         ScaniaCRMExport.dbo.email

  155   versionnumber                         bigint             Yes     Column versionnumber from
                                                                         ScaniaCRMExport.dbo.email

  156   DataSourceId                          int                Yes     Id of the data source the row comes
                                                                         from

  157   ThreadLogId                           int                Yes     Id of ThreadLog which inserted the
                                                                         row
  ------------------------------------------------------------------------------------------------------------

\[Back to table list\]\[listoftables\]
