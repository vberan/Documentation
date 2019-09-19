Table Stage.CRMdboSystemuser {#tblStageCRMdboSystemuser}
----------------------------

Description:

Stage table CRMdboSystemuser.

List of dependent objects:

-   \[Stage.uspLoadCRMdboSystemuser\]\[spStageuspLoadCRMdboSystemuser\]

-   \[Vault.uspLoadCRMdboSystemuser\]\[spVaultuspLoadCRMdboSystemuser\]

  ----------------------------------------------------------------------------------------------------------
  Id    Column Name                          Data Type          Allow   Description
                                                                Nulls   
  ----- ------------------------------------ ------------------ ------- ------------------------------------
  1     accessmode                           int                Yes     Column accessmode from
                                                                        ScaniaCRMExport.dbo.systemuser

  2     activedirectoryguid                  uniqueidentifier   Yes     Column activedirectoryguid from
                                                                        ScaniaCRMExport.dbo.systemuser

  3     address1\_addressid                  uniqueidentifier   Yes     Column address1\_addressid from
                                                                        ScaniaCRMExport.dbo.systemuser

  4     address1\_addresstypecode            int                Yes     Column address1\_addresstypecode
                                                                        from ScaniaCRMExport.dbo.systemuser

  5     address1\_city                       nvarchar(512)      Yes     Column address1\_city from
                                                                        ScaniaCRMExport.dbo.systemuser

  6     address1\_composite                  nvarchar(max)      Yes     Column address1\_composite from
                                                                        ScaniaCRMExport.dbo.systemuser

  7     address1\_country                    nvarchar(512)      Yes     Column address1\_country from
                                                                        ScaniaCRMExport.dbo.systemuser

  8     address1\_county                     nvarchar(512)      Yes     Column address1\_county from
                                                                        ScaniaCRMExport.dbo.systemuser

  9     address1\_fax                        nvarchar(256)      Yes     Column address1\_fax from
                                                                        ScaniaCRMExport.dbo.systemuser

  10    address1\_latitude                   decimal            Yes     Column address1\_latitude from
                                                                        ScaniaCRMExport.dbo.systemuser

  11    address1\_line1                      nvarchar(max)      Yes     Column address1\_line1 from
                                                                        ScaniaCRMExport.dbo.systemuser

  12    address1\_line2                      nvarchar(max)      Yes     Column address1\_line2 from
                                                                        ScaniaCRMExport.dbo.systemuser

  13    address1\_line3                      nvarchar(max)      Yes     Column address1\_line3 from
                                                                        ScaniaCRMExport.dbo.systemuser

  14    address1\_longitude                  decimal            Yes     Column address1\_longitude from
                                                                        ScaniaCRMExport.dbo.systemuser

  15    address1\_name                       nvarchar(400)      Yes     Column address1\_name from
                                                                        ScaniaCRMExport.dbo.systemuser

  16    address1\_postalcode                 nvarchar(160)      Yes     Column address1\_postalcode from
                                                                        ScaniaCRMExport.dbo.systemuser

  17    address1\_postofficebox              nvarchar(160)      Yes     Column address1\_postofficebox from
                                                                        ScaniaCRMExport.dbo.systemuser

  18    address1\_shippingmethodcode         int                Yes     Column address1\_shippingmethodcode
                                                                        from ScaniaCRMExport.dbo.systemuser

  19    address1\_stateorprovince            nvarchar(512)      Yes     Column address1\_stateorprovince
                                                                        from ScaniaCRMExport.dbo.systemuser

  20    address1\_telephone1                 nvarchar(256)      Yes     Column address1\_telephone1 from
                                                                        ScaniaCRMExport.dbo.systemuser

  21    address1\_telephone2                 nvarchar(200)      Yes     Column address1\_telephone2 from
                                                                        ScaniaCRMExport.dbo.systemuser

  22    address1\_telephone3                 nvarchar(200)      Yes     Column address1\_telephone3 from
                                                                        ScaniaCRMExport.dbo.systemuser

  23    address1\_upszone                    nvarchar(16)       Yes     Column address1\_upszone from
                                                                        ScaniaCRMExport.dbo.systemuser

  24    address1\_utcoffset                  int                Yes     Column address1\_utcoffset from
                                                                        ScaniaCRMExport.dbo.systemuser

  25    address2\_addressid                  uniqueidentifier   Yes     Column address2\_addressid from
                                                                        ScaniaCRMExport.dbo.systemuser

  26    address2\_addresstypecode            int                Yes     Column address2\_addresstypecode
                                                                        from ScaniaCRMExport.dbo.systemuser

  27    address2\_city                       nvarchar(512)      Yes     Column address2\_city from
                                                                        ScaniaCRMExport.dbo.systemuser

  28    address2\_composite                  nvarchar(max)      Yes     Column address2\_composite from
                                                                        ScaniaCRMExport.dbo.systemuser

  29    address2\_country                    nvarchar(512)      Yes     Column address2\_country from
                                                                        ScaniaCRMExport.dbo.systemuser

  30    address2\_county                     nvarchar(512)      Yes     Column address2\_county from
                                                                        ScaniaCRMExport.dbo.systemuser

  31    address2\_fax                        nvarchar(200)      Yes     Column address2\_fax from
                                                                        ScaniaCRMExport.dbo.systemuser

  32    address2\_latitude                   decimal            Yes     Column address2\_latitude from
                                                                        ScaniaCRMExport.dbo.systemuser

  33    address2\_line1                      nvarchar(max)      Yes     Column address2\_line1 from
                                                                        ScaniaCRMExport.dbo.systemuser

  34    address2\_line2                      nvarchar(max)      Yes     Column address2\_line2 from
                                                                        ScaniaCRMExport.dbo.systemuser

  35    address2\_line3                      nvarchar(max)      Yes     Column address2\_line3 from
                                                                        ScaniaCRMExport.dbo.systemuser

  36    address2\_longitude                  decimal            Yes     Column address2\_longitude from
                                                                        ScaniaCRMExport.dbo.systemuser

  37    address2\_name                       nvarchar(400)      Yes     Column address2\_name from
                                                                        ScaniaCRMExport.dbo.systemuser

  38    address2\_postalcode                 nvarchar(160)      Yes     Column address2\_postalcode from
                                                                        ScaniaCRMExport.dbo.systemuser

  39    address2\_postofficebox              nvarchar(160)      Yes     Column address2\_postofficebox from
                                                                        ScaniaCRMExport.dbo.systemuser

  40    address2\_shippingmethodcode         int                Yes     Column address2\_shippingmethodcode
                                                                        from ScaniaCRMExport.dbo.systemuser

  41    address2\_stateorprovince            nvarchar(512)      Yes     Column address2\_stateorprovince
                                                                        from ScaniaCRMExport.dbo.systemuser

  42    address2\_telephone1                 nvarchar(200)      Yes     Column address2\_telephone1 from
                                                                        ScaniaCRMExport.dbo.systemuser

  43    address2\_telephone2                 nvarchar(200)      Yes     Column address2\_telephone2 from
                                                                        ScaniaCRMExport.dbo.systemuser

  44    address2\_telephone3                 nvarchar(200)      Yes     Column address2\_telephone3 from
                                                                        ScaniaCRMExport.dbo.systemuser

  45    address2\_upszone                    nvarchar(16)       Yes     Column address2\_upszone from
                                                                        ScaniaCRMExport.dbo.systemuser

  46    address2\_utcoffset                  int                Yes     Column address2\_utcoffset from
                                                                        ScaniaCRMExport.dbo.systemuser

  47    applicationid                        uniqueidentifier   Yes     Column applicationid from
                                                                        ScaniaCRMExport.dbo.systemuser

  48    applicationiduri                     nvarchar(max)      Yes     Column applicationiduri from
                                                                        ScaniaCRMExport.dbo.systemuser

  49    azureactivedirectoryobjectid         uniqueidentifier   Yes     Column azureactivedirectoryobjectid
                                                                        from ScaniaCRMExport.dbo.systemuser

  50    businessunitid                       uniqueidentifier   Yes     Column businessunitid from
                                                                        ScaniaCRMExport.dbo.systemuser

  51    businessunitid\_entitytype           nvarchar(512)      Yes     Column businessunitid\_entitytype
                                                                        from ScaniaCRMExport.dbo.systemuser

  52    businessunitidname                   nvarchar(400)      Yes     Column businessunitidname from
                                                                        ScaniaCRMExport.dbo.systemuser

  53    calendarid                           uniqueidentifier   Yes     Column calendarid from
                                                                        ScaniaCRMExport.dbo.systemuser

  54    calendarid\_entitytype               nvarchar(512)      Yes     Column calendarid\_entitytype from
                                                                        ScaniaCRMExport.dbo.systemuser

  55    caltype                              int                Yes     Column caltype from
                                                                        ScaniaCRMExport.dbo.systemuser

  56    createdby                            uniqueidentifier   Yes     Column createdby from
                                                                        ScaniaCRMExport.dbo.systemuser

  57    createdby\_entitytype                nvarchar(512)      Yes     Column createdby\_entitytype from
                                                                        ScaniaCRMExport.dbo.systemuser

  58    createdbyname                        nvarchar(400)      Yes     Column createdbyname from
                                                                        ScaniaCRMExport.dbo.systemuser

  59    createdbyyominame                    nvarchar(400)      Yes     Column createdbyyominame from
                                                                        ScaniaCRMExport.dbo.systemuser

  60    createdon                            datetime           Yes     Column createdon from
                                                                        ScaniaCRMExport.dbo.systemuser

  61    createdonbehalfby                    uniqueidentifier   Yes     Column createdonbehalfby from
                                                                        ScaniaCRMExport.dbo.systemuser

  62    createdonbehalfby\_entitytype        nvarchar(512)      Yes     Column createdonbehalfby\_entitytype
                                                                        from ScaniaCRMExport.dbo.systemuser

  63    createdonbehalfbyname                nvarchar(400)      Yes     Column createdonbehalfbyname from
                                                                        ScaniaCRMExport.dbo.systemuser

  64    createdonbehalfbyyominame            nvarchar(400)      Yes     Column createdonbehalfbyyominame
                                                                        from ScaniaCRMExport.dbo.systemuser

  65    defaultfilterspopulated              bit                Yes     Column defaultfilterspopulated from
                                                                        ScaniaCRMExport.dbo.systemuser

  66    defaultmailbox                       uniqueidentifier   Yes     Column defaultmailbox from
                                                                        ScaniaCRMExport.dbo.systemuser

  67    defaultmailbox\_entitytype           nvarchar(512)      Yes     Column defaultmailbox\_entitytype
                                                                        from ScaniaCRMExport.dbo.systemuser

  68    defaultmailboxname                   nvarchar(400)      Yes     Column defaultmailboxname from
                                                                        ScaniaCRMExport.dbo.systemuser

  69    defaultodbfoldername                 nvarchar(800)      Yes     Column defaultodbfoldername from
                                                                        ScaniaCRMExport.dbo.systemuser

  70    disabledreason                       nvarchar(2000)     Yes     Column disabledreason from
                                                                        ScaniaCRMExport.dbo.systemuser

  71    displayinserviceviews                bit                Yes     Column displayinserviceviews from
                                                                        ScaniaCRMExport.dbo.systemuser

  72    domainname                           nvarchar(max)      Yes     Column domainname from
                                                                        ScaniaCRMExport.dbo.systemuser

  73    emailrouteraccessapproval            int                Yes     Column emailrouteraccessapproval
                                                                        from ScaniaCRMExport.dbo.systemuser

  74    employeeid                           nvarchar(400)      Yes     Column employeeid from
                                                                        ScaniaCRMExport.dbo.systemuser

  75    entityimage\_timestamp               bigint             Yes     Column entityimage\_timestamp from
                                                                        ScaniaCRMExport.dbo.systemuser

  76    entityimage\_url                     nvarchar(800)      Yes     Column entityimage\_url from
                                                                        ScaniaCRMExport.dbo.systemuser

  77    entityimageid                        uniqueidentifier   Yes     Column entityimageid from
                                                                        ScaniaCRMExport.dbo.systemuser

  78    exchangerate                         decimal            Yes     Column exchangerate from
                                                                        ScaniaCRMExport.dbo.systemuser

  79    firstname                            nvarchar(256)      Yes     Column firstname from
                                                                        ScaniaCRMExport.dbo.systemuser

  80    fullname                             nvarchar(800)      Yes     Column fullname from
                                                                        ScaniaCRMExport.dbo.systemuser

  81    governmentid                         nvarchar(400)      Yes     Column governmentid from
                                                                        ScaniaCRMExport.dbo.systemuser

  82    homephone                            nvarchar(200)      Yes     Column homephone from
                                                                        ScaniaCRMExport.dbo.systemuser

  83    Id                                   uniqueidentifier   Yes     Column Id from
                                                                        ScaniaCRMExport.dbo.systemuser

  84    identityid                           int                Yes     Column identityid from
                                                                        ScaniaCRMExport.dbo.systemuser

  85    importsequencenumber                 int                Yes     Column importsequencenumber from
                                                                        ScaniaCRMExport.dbo.systemuser

  86    incomingemaildeliverymethod          int                Yes     Column incomingemaildeliverymethod
                                                                        from ScaniaCRMExport.dbo.systemuser

  87    internalemailaddress                 nvarchar(400)      Yes     Column internalemailaddress from
                                                                        ScaniaCRMExport.dbo.systemuser

  88    invitestatuscode                     int                Yes     Column invitestatuscode from
                                                                        ScaniaCRMExport.dbo.systemuser

  89    isactivedirectoryuser                bit                Yes     Column isactivedirectoryuser from
                                                                        ScaniaCRMExport.dbo.systemuser

  90    isdisabled                           bit                Yes     Column isdisabled from
                                                                        ScaniaCRMExport.dbo.systemuser

  91    isemailaddressapprovedbyo365admin    bit                Yes     Column
                                                                        isemailaddressapprovedbyo365admin
                                                                        from ScaniaCRMExport.dbo.systemuser

  92    isintegrationuser                    bit                Yes     Column isintegrationuser from
                                                                        ScaniaCRMExport.dbo.systemuser

  93    islicensed                           bit                Yes     Column islicensed from
                                                                        ScaniaCRMExport.dbo.systemuser

  94    issyncwithdirectory                  bit                Yes     Column issyncwithdirectory from
                                                                        ScaniaCRMExport.dbo.systemuser

  95    jobtitle                             nvarchar(400)      Yes     Column jobtitle from
                                                                        ScaniaCRMExport.dbo.systemuser

  96    lastname                             nvarchar(256)      Yes     Column lastname from
                                                                        ScaniaCRMExport.dbo.systemuser

  97    latestupdatetime                     datetime           Yes     Column latestupdatetime from
                                                                        ScaniaCRMExport.dbo.systemuser

  98    llp\_arbesdbname                     nvarchar(400)      Yes     Column llp\_arbesdbname from
                                                                        ScaniaCRMExport.dbo.systemuser

  99    llp\_arbessyncallowed                bit                Yes     Column llp\_arbessyncallowed from
                                                                        ScaniaCRMExport.dbo.systemuser

  100   llp\_automastersyncallowed           bit                Yes     Column llp\_automastersyncallowed
                                                                        from ScaniaCRMExport.dbo.systemuser

  101   llp\_automastersyncdbname            nvarchar(400)      Yes     Column llp\_automastersyncdbname
                                                                        from ScaniaCRMExport.dbo.systemuser

  102   llp\_automaticallysendtoautomaster   bit                Yes     Column
                                                                        llp\_automaticallysendtoautomaster
                                                                        from ScaniaCRMExport.dbo.systemuser

  103   llp\_certsyncallowed                 bit                Yes     Column llp\_certsyncallowed from
                                                                        ScaniaCRMExport.dbo.systemuser

  104   llp\_certsyncdbname                  nvarchar(400)      Yes     Column llp\_certsyncdbname from
                                                                        ScaniaCRMExport.dbo.systemuser

  105   llp\_defaultopportunitytype          int                Yes     Column llp\_defaultopportunitytype
                                                                        from ScaniaCRMExport.dbo.systemuser

  106   llp\_idnetsuite                      int                Yes     Column llp\_idnetsuite from
                                                                        ScaniaCRMExport.dbo.systemuser

  107   llp\_sfinsuranceid                   uniqueidentifier   Yes     Column llp\_sfinsuranceid from
                                                                        ScaniaCRMExport.dbo.systemuser

  108   llp\_sfinsuranceid\_entitytype       nvarchar(512)      Yes     Column
                                                                        llp\_sfinsuranceid\_entitytype from
                                                                        ScaniaCRMExport.dbo.systemuser

  109   llp\_sfinsuranceidname               nvarchar(800)      Yes     Column llp\_sfinsuranceidname from
                                                                        ScaniaCRMExport.dbo.systemuser

  110   llp\_sfinsuranceidyominame           nvarchar(800)      Yes     Column llp\_sfinsuranceidyominame
                                                                        from ScaniaCRMExport.dbo.systemuser

  111   llp\_sfsalespersonid                 uniqueidentifier   Yes     Column llp\_sfsalespersonid from
                                                                        ScaniaCRMExport.dbo.systemuser

  112   llp\_sfsalespersonid\_entitytype     nvarchar(512)      Yes     Column
                                                                        llp\_sfsalespersonid\_entitytype
                                                                        from ScaniaCRMExport.dbo.systemuser

  113   llp\_sfsalespersonidname             nvarchar(400)      Yes     Column llp\_sfsalespersonidname from
                                                                        ScaniaCRMExport.dbo.systemuser

  114   llp\_sfsalespersonidyominame         nvarchar(400)      Yes     Column llp\_sfsalespersonidyominame
                                                                        from ScaniaCRMExport.dbo.systemuser

  115   llp\_sportlanguage                   int                Yes     Column llp\_sportlanguage from
                                                                        ScaniaCRMExport.dbo.systemuser

  116   llp\_sportsellergroup                nvarchar(400)      Yes     Column llp\_sportsellergroup from
                                                                        ScaniaCRMExport.dbo.systemuser

  117   llp\_sportsellerorganization         nvarchar(400)      Yes     Column llp\_sportsellerorganization
                                                                        from ScaniaCRMExport.dbo.systemuser

  118   llp\_utsalespersonid                 uniqueidentifier   Yes     Column llp\_utsalespersonid from
                                                                        ScaniaCRMExport.dbo.systemuser

  119   llp\_utsalespersonid\_entitytype     nvarchar(512)      Yes     Column
                                                                        llp\_utsalespersonid\_entitytype
                                                                        from ScaniaCRMExport.dbo.systemuser

  120   llp\_utsalespersonidname             nvarchar(400)      Yes     Column llp\_utsalespersonidname from
                                                                        ScaniaCRMExport.dbo.systemuser

  121   llp\_utsalespersonidyominame         nvarchar(400)      Yes     Column llp\_utsalespersonidyominame
                                                                        from ScaniaCRMExport.dbo.systemuser

  122   llp\_xdslogin                        nvarchar(400)      Yes     Column llp\_xdslogin from
                                                                        ScaniaCRMExport.dbo.systemuser

  123   middlename                           nvarchar(200)      Yes     Column middlename from
                                                                        ScaniaCRMExport.dbo.systemuser

  124   mobilealertemail                     nvarchar(400)      Yes     Column mobilealertemail from
                                                                        ScaniaCRMExport.dbo.systemuser

  125   mobileofflineprofileid               uniqueidentifier   Yes     Column mobileofflineprofileid from
                                                                        ScaniaCRMExport.dbo.systemuser

  126   mobileofflineprofileid\_entitytype   nvarchar(512)      Yes     Column
                                                                        mobileofflineprofileid\_entitytype
                                                                        from ScaniaCRMExport.dbo.systemuser

  127   mobileofflineprofileidname           nvarchar(400)      Yes     Column mobileofflineprofileidname
                                                                        from ScaniaCRMExport.dbo.systemuser

  128   mobilephone                          nvarchar(256)      Yes     Column mobilephone from
                                                                        ScaniaCRMExport.dbo.systemuser

  129   modifiedby                           uniqueidentifier   Yes     Column modifiedby from
                                                                        ScaniaCRMExport.dbo.systemuser

  130   modifiedby\_entitytype               nvarchar(512)      Yes     Column modifiedby\_entitytype from
                                                                        ScaniaCRMExport.dbo.systemuser

  131   modifiedbyname                       nvarchar(400)      Yes     Column modifiedbyname from
                                                                        ScaniaCRMExport.dbo.systemuser

  132   modifiedbyyominame                   nvarchar(400)      Yes     Column modifiedbyyominame from
                                                                        ScaniaCRMExport.dbo.systemuser

  133   modifiedon                           datetime           Yes     Column modifiedon from
                                                                        ScaniaCRMExport.dbo.systemuser

  134   modifiedonbehalfby                   uniqueidentifier   Yes     Column modifiedonbehalfby from
                                                                        ScaniaCRMExport.dbo.systemuser

  135   modifiedonbehalfby\_entitytype       nvarchar(512)      Yes     Column
                                                                        modifiedonbehalfby\_entitytype from
                                                                        ScaniaCRMExport.dbo.systemuser

  136   modifiedonbehalfbyname               nvarchar(400)      Yes     Column modifiedonbehalfbyname from
                                                                        ScaniaCRMExport.dbo.systemuser

  137   modifiedonbehalfbyyominame           nvarchar(400)      Yes     Column modifiedonbehalfbyyominame
                                                                        from ScaniaCRMExport.dbo.systemuser

  138   msdyn\_gdproptout                    bit                Yes     Column msdyn\_gdproptout from
                                                                        ScaniaCRMExport.dbo.systemuser

  139   nickname                             nvarchar(200)      Yes     Column nickname from
                                                                        ScaniaCRMExport.dbo.systemuser

  140   organizationid                       uniqueidentifier   Yes     Column organizationid from
                                                                        ScaniaCRMExport.dbo.systemuser

  141   organizationidname                   nvarchar(400)      Yes     Column organizationidname from
                                                                        ScaniaCRMExport.dbo.systemuser

  142   outgoingemaildeliverymethod          int                Yes     Column outgoingemaildeliverymethod
                                                                        from ScaniaCRMExport.dbo.systemuser

  143   overriddencreatedon                  datetime           Yes     Column overriddencreatedon from
                                                                        ScaniaCRMExport.dbo.systemuser

  144   parentsystemuserid                   uniqueidentifier   Yes     Column parentsystemuserid from
                                                                        ScaniaCRMExport.dbo.systemuser

  145   parentsystemuserid\_entitytype       nvarchar(512)      Yes     Column
                                                                        parentsystemuserid\_entitytype from
                                                                        ScaniaCRMExport.dbo.systemuser

  146   parentsystemuseridname               nvarchar(400)      Yes     Column parentsystemuseridname from
                                                                        ScaniaCRMExport.dbo.systemuser

  147   parentsystemuseridyominame           nvarchar(400)      Yes     Column parentsystemuseridyominame
                                                                        from ScaniaCRMExport.dbo.systemuser

  148   passporthi                           int                Yes     Column passporthi from
                                                                        ScaniaCRMExport.dbo.systemuser

  149   passportlo                           int                Yes     Column passportlo from
                                                                        ScaniaCRMExport.dbo.systemuser

  150   personalemailaddress                 nvarchar(400)      Yes     Column personalemailaddress from
                                                                        ScaniaCRMExport.dbo.systemuser

  151   photourl                             nvarchar(800)      Yes     Column photourl from
                                                                        ScaniaCRMExport.dbo.systemuser

  152   positionid                           uniqueidentifier   Yes     Column positionid from
                                                                        ScaniaCRMExport.dbo.systemuser

  153   positionid\_entitytype               nvarchar(512)      Yes     Column positionid\_entitytype from
                                                                        ScaniaCRMExport.dbo.systemuser

  154   positionidname                       nvarchar(400)      Yes     Column positionidname from
                                                                        ScaniaCRMExport.dbo.systemuser

  155   preferredaddresscode                 int                Yes     Column preferredaddresscode from
                                                                        ScaniaCRMExport.dbo.systemuser

  156   preferredemailcode                   int                Yes     Column preferredemailcode from
                                                                        ScaniaCRMExport.dbo.systemuser

  157   preferredphonecode                   int                Yes     Column preferredphonecode from
                                                                        ScaniaCRMExport.dbo.systemuser

  158   processid                            uniqueidentifier   Yes     Column processid from
                                                                        ScaniaCRMExport.dbo.systemuser

  159   queueid                              uniqueidentifier   Yes     Column queueid from
                                                                        ScaniaCRMExport.dbo.systemuser

  160   queueid\_entitytype                  nvarchar(512)      Yes     Column queueid\_entitytype from
                                                                        ScaniaCRMExport.dbo.systemuser

  161   queueidname                          nvarchar(1600)     Yes     Column queueidname from
                                                                        ScaniaCRMExport.dbo.systemuser

  162   salutation                           nvarchar(80)       Yes     Column salutation from
                                                                        ScaniaCRMExport.dbo.systemuser

  163   setupuser                            bit                Yes     Column setupuser from
                                                                        ScaniaCRMExport.dbo.systemuser

  164   sharepointemailaddress               nvarchar(max)      Yes     Column sharepointemailaddress from
                                                                        ScaniaCRMExport.dbo.systemuser

  165   SinkCreatedOn                        datetime           Yes     Column SinkCreatedOn from
                                                                        ScaniaCRMExport.dbo.systemuser

  166   SinkModifiedOn                       datetime           Yes     Column SinkModifiedOn from
                                                                        ScaniaCRMExport.dbo.systemuser

  167   siteid                               uniqueidentifier   Yes     Column siteid from
                                                                        ScaniaCRMExport.dbo.systemuser

  168   siteid\_entitytype                   nvarchar(512)      Yes     Column siteid\_entitytype from
                                                                        ScaniaCRMExport.dbo.systemuser

  169   siteidname                           nvarchar(400)      Yes     Column siteidname from
                                                                        ScaniaCRMExport.dbo.systemuser

  170   skills                               nvarchar(400)      Yes     Column skills from
                                                                        ScaniaCRMExport.dbo.systemuser

  171   stageid                              uniqueidentifier   Yes     Column stageid from
                                                                        ScaniaCRMExport.dbo.systemuser

  172   systemuserid                         uniqueidentifier   Yes     Column systemuserid from
                                                                        ScaniaCRMExport.dbo.systemuser

  173   territoryid                          uniqueidentifier   Yes     Column territoryid from
                                                                        ScaniaCRMExport.dbo.systemuser

  174   territoryid\_entitytype              nvarchar(512)      Yes     Column territoryid\_entitytype from
                                                                        ScaniaCRMExport.dbo.systemuser

  175   territoryidname                      nvarchar(400)      Yes     Column territoryidname from
                                                                        ScaniaCRMExport.dbo.systemuser

  176   timezoneruleversionnumber            int                Yes     Column timezoneruleversionnumber
                                                                        from ScaniaCRMExport.dbo.systemuser

  177   title                                nvarchar(512)      Yes     Column title from
                                                                        ScaniaCRMExport.dbo.systemuser

  178   transactioncurrencyid                uniqueidentifier   Yes     Column transactioncurrencyid from
                                                                        ScaniaCRMExport.dbo.systemuser

  179   transactioncurrencyid\_entitytype    nvarchar(512)      Yes     Column
                                                                        transactioncurrencyid\_entitytype
                                                                        from ScaniaCRMExport.dbo.systemuser

  180   transactioncurrencyidname            nvarchar(400)      Yes     Column transactioncurrencyidname
                                                                        from ScaniaCRMExport.dbo.systemuser

  181   traversedpath                        nvarchar(max)      Yes     Column traversedpath from
                                                                        ScaniaCRMExport.dbo.systemuser

  182   userlicensetype                      int                Yes     Column userlicensetype from
                                                                        ScaniaCRMExport.dbo.systemuser

  183   userpuid                             nvarchar(400)      Yes     Column userpuid from
                                                                        ScaniaCRMExport.dbo.systemuser

  184   utcconversiontimezonecode            int                Yes     Column utcconversiontimezonecode
                                                                        from ScaniaCRMExport.dbo.systemuser

  185   versionnumber                        bigint             Yes     Column versionnumber from
                                                                        ScaniaCRMExport.dbo.systemuser

  186   windowsliveid                        nvarchar(max)      Yes     Column windowsliveid from
                                                                        ScaniaCRMExport.dbo.systemuser

  187   yammeremailaddress                   nvarchar(800)      Yes     Column yammeremailaddress from
                                                                        ScaniaCRMExport.dbo.systemuser

  188   yammeruserid                         nvarchar(512)      Yes     Column yammeruserid from
                                                                        ScaniaCRMExport.dbo.systemuser

  189   yomifirstname                        nvarchar(256)      Yes     Column yomifirstname from
                                                                        ScaniaCRMExport.dbo.systemuser

  190   yomifullname                         nvarchar(800)      Yes     Column yomifullname from
                                                                        ScaniaCRMExport.dbo.systemuser

  191   yomilastname                         nvarchar(256)      Yes     Column yomilastname from
                                                                        ScaniaCRMExport.dbo.systemuser

  192   yomimiddlename                       nvarchar(200)      Yes     Column yomimiddlename from
                                                                        ScaniaCRMExport.dbo.systemuser

  193   DataSourceId                         int                Yes     Id of the data source the row comes
                                                                        from

  194   ThreadLogId                          int                Yes     Id of ThreadLog which inserted the
                                                                        row
  ----------------------------------------------------------------------------------------------------------

\[Back to table list\]\[listoftables\]
