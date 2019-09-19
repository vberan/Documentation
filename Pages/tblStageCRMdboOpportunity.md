Table Stage.CRMdboOpportunity {#tblStageCRMdboOpportunity}
-----------------------------

Description:

Stage table CRMdboOpportunity.

List of dependent objects:

-   \[Stage.uspLoadCRMdboOpportunity\]\[spStageuspLoadCRMdboOpportunity\]

-   \[Vault.uspLoadCRMdboOpportunity\]\[spVaultuspLoadCRMdboOpportunity\]

  ----------------------------------------------------------------------------------------------------------------------------------
  Id    Column Name                                      Data Type          Allow   Description
                                                                            Nulls   
  ----- ------------------------------------------------ ------------------ ------- ------------------------------------------------
  1     accountid                                        uniqueidentifier   Yes     Column accountid from
                                                                                    ScaniaCRMExport.dbo.opportunity

  2     accountid\_entitytype                            nvarchar(512)      Yes     Column accountid\_entitytype from
                                                                                    ScaniaCRMExport.dbo.opportunity

  3     accountidname                                    nvarchar(400)      Yes     Column accountidname from
                                                                                    ScaniaCRMExport.dbo.opportunity

  4     accountidyominame                                nvarchar(400)      Yes     Column accountidyominame from
                                                                                    ScaniaCRMExport.dbo.opportunity

  5     actualclosedate                                  datetime           Yes     Column actualclosedate from
                                                                                    ScaniaCRMExport.dbo.opportunity

  6     actualvalue                                      decimal            Yes     Column actualvalue from
                                                                                    ScaniaCRMExport.dbo.opportunity

  7     actualvalue\_base                                decimal            Yes     Column actualvalue\_base from
                                                                                    ScaniaCRMExport.dbo.opportunity

  8     budgetamount                                     decimal            Yes     Column budgetamount from
                                                                                    ScaniaCRMExport.dbo.opportunity

  9     budgetamount\_base                               decimal            Yes     Column budgetamount\_base from
                                                                                    ScaniaCRMExport.dbo.opportunity

  10    budgetstatus                                     int                Yes     Column budgetstatus from
                                                                                    ScaniaCRMExport.dbo.opportunity

  11    campaignid                                       uniqueidentifier   Yes     Column campaignid from
                                                                                    ScaniaCRMExport.dbo.opportunity

  12    campaignid\_entitytype                           nvarchar(512)      Yes     Column campaignid\_entitytype from
                                                                                    ScaniaCRMExport.dbo.opportunity

  13    campaignidname                                   nvarchar(400)      Yes     Column campaignidname from
                                                                                    ScaniaCRMExport.dbo.opportunity

  14    captureproposalfeedback                          bit                Yes     Column captureproposalfeedback from
                                                                                    ScaniaCRMExport.dbo.opportunity

  15    closeprobability                                 int                Yes     Column closeprobability from
                                                                                    ScaniaCRMExport.dbo.opportunity

  16    completefinalproposal                            bit                Yes     Column completefinalproposal from
                                                                                    ScaniaCRMExport.dbo.opportunity

  17    completeinternalreview                           bit                Yes     Column completeinternalreview from
                                                                                    ScaniaCRMExport.dbo.opportunity

  18    confirminterest                                  bit                Yes     Column confirminterest from
                                                                                    ScaniaCRMExport.dbo.opportunity

  19    contactid                                        uniqueidentifier   Yes     Column contactid from
                                                                                    ScaniaCRMExport.dbo.opportunity

  20    contactid\_entitytype                            nvarchar(512)      Yes     Column contactid\_entitytype from
                                                                                    ScaniaCRMExport.dbo.opportunity

  21    contactidname                                    nvarchar(400)      Yes     Column contactidname from
                                                                                    ScaniaCRMExport.dbo.opportunity

  22    contactidyominame                                nvarchar(400)      Yes     Column contactidyominame from
                                                                                    ScaniaCRMExport.dbo.opportunity

  23    createdby                                        uniqueidentifier   Yes     Column createdby from
                                                                                    ScaniaCRMExport.dbo.opportunity

  24    createdby\_entitytype                            nvarchar(512)      Yes     Column createdby\_entitytype from
                                                                                    ScaniaCRMExport.dbo.opportunity

  25    createdbyname                                    nvarchar(400)      Yes     Column createdbyname from
                                                                                    ScaniaCRMExport.dbo.opportunity

  26    createdbyyominame                                nvarchar(400)      Yes     Column createdbyyominame from
                                                                                    ScaniaCRMExport.dbo.opportunity

  27    createdon                                        datetime           Yes     Column createdon from
                                                                                    ScaniaCRMExport.dbo.opportunity

  28    createdonbehalfby                                uniqueidentifier   Yes     Column createdonbehalfby from
                                                                                    ScaniaCRMExport.dbo.opportunity

  29    createdonbehalfby\_entitytype                    nvarchar(512)      Yes     Column createdonbehalfby\_entitytype from
                                                                                    ScaniaCRMExport.dbo.opportunity

  30    createdonbehalfbyname                            nvarchar(400)      Yes     Column createdonbehalfbyname from
                                                                                    ScaniaCRMExport.dbo.opportunity

  31    createdonbehalfbyyominame                        nvarchar(400)      Yes     Column createdonbehalfbyyominame from
                                                                                    ScaniaCRMExport.dbo.opportunity

  32    currentsituation                                 nvarchar(max)      Yes     Column currentsituation from
                                                                                    ScaniaCRMExport.dbo.opportunity

  33    customerid                                       uniqueidentifier   Yes     Column customerid from
                                                                                    ScaniaCRMExport.dbo.opportunity

  34    customerid\_entitytype                           nvarchar(512)      Yes     Column customerid\_entitytype from
                                                                                    ScaniaCRMExport.dbo.opportunity

  35    customeridname                                   nvarchar(640)      Yes     Column customeridname from
                                                                                    ScaniaCRMExport.dbo.opportunity

  36    customeridtype                                   nvarchar(max)      Yes     Column customeridtype from
                                                                                    ScaniaCRMExport.dbo.opportunity

  37    customeridyominame                               nvarchar(1800)     Yes     Column customeridyominame from
                                                                                    ScaniaCRMExport.dbo.opportunity

  38    customerneed                                     nvarchar(max)      Yes     Column customerneed from
                                                                                    ScaniaCRMExport.dbo.opportunity

  39    customerpainpoints                               nvarchar(max)      Yes     Column customerpainpoints from
                                                                                    ScaniaCRMExport.dbo.opportunity

  40    decisionmaker                                    bit                Yes     Column decisionmaker from
                                                                                    ScaniaCRMExport.dbo.opportunity

  41    description                                      nvarchar(max)      Yes     Column description from
                                                                                    ScaniaCRMExport.dbo.opportunity

  42    developproposal                                  bit                Yes     Column developproposal from
                                                                                    ScaniaCRMExport.dbo.opportunity

  43    discountamount                                   decimal            Yes     Column discountamount from
                                                                                    ScaniaCRMExport.dbo.opportunity

  44    discountamount\_base                             decimal            Yes     Column discountamount\_base from
                                                                                    ScaniaCRMExport.dbo.opportunity

  45    discountpercentage                               decimal            Yes     Column discountpercentage from
                                                                                    ScaniaCRMExport.dbo.opportunity

  46    emailaddress                                     nvarchar(400)      Yes     Column emailaddress from
                                                                                    ScaniaCRMExport.dbo.opportunity

  47    estimatedclosedate                               datetime           Yes     Column estimatedclosedate from
                                                                                    ScaniaCRMExport.dbo.opportunity

  48    estimatedvalue                                   decimal            Yes     Column estimatedvalue from
                                                                                    ScaniaCRMExport.dbo.opportunity

  49    estimatedvalue\_base                             decimal            Yes     Column estimatedvalue\_base from
                                                                                    ScaniaCRMExport.dbo.opportunity

  50    evaluatefit                                      bit                Yes     Column evaluatefit from
                                                                                    ScaniaCRMExport.dbo.opportunity

  51    exchangerate                                     decimal            Yes     Column exchangerate from
                                                                                    ScaniaCRMExport.dbo.opportunity

  52    filedebrief                                      bit                Yes     Column filedebrief from
                                                                                    ScaniaCRMExport.dbo.opportunity

  53    finaldecisiondate                                datetime           Yes     Column finaldecisiondate from
                                                                                    ScaniaCRMExport.dbo.opportunity

  54    freightamount                                    decimal            Yes     Column freightamount from
                                                                                    ScaniaCRMExport.dbo.opportunity

  55    freightamount\_base                              decimal            Yes     Column freightamount\_base from
                                                                                    ScaniaCRMExport.dbo.opportunity

  56    Id                                               uniqueidentifier   Yes     Column Id from ScaniaCRMExport.dbo.opportunity

  57    identifycompetitors                              bit                Yes     Column identifycompetitors from
                                                                                    ScaniaCRMExport.dbo.opportunity

  58    identifycustomercontacts                         bit                Yes     Column identifycustomercontacts from
                                                                                    ScaniaCRMExport.dbo.opportunity

  59    identifypursuitteam                              bit                Yes     Column identifypursuitteam from
                                                                                    ScaniaCRMExport.dbo.opportunity

  60    importsequencenumber                             int                Yes     Column importsequencenumber from
                                                                                    ScaniaCRMExport.dbo.opportunity

  61    initialcommunication                             int                Yes     Column initialcommunication from
                                                                                    ScaniaCRMExport.dbo.opportunity

  62    isprivate                                        bit                Yes     Column isprivate from
                                                                                    ScaniaCRMExport.dbo.opportunity

  63    isrevenuesystemcalculated                        bit                Yes     Column isrevenuesystemcalculated from
                                                                                    ScaniaCRMExport.dbo.opportunity

  64    lastonholdtime                                   datetime           Yes     Column lastonholdtime from
                                                                                    ScaniaCRMExport.dbo.opportunity

  65    llp\_add                                         datetime           Yes     Column llp\_add from
                                                                                    ScaniaCRMExport.dbo.opportunity

  66    llp\_agreedhandoverdate                          datetime           Yes     Column llp\_agreedhandoverdate from
                                                                                    ScaniaCRMExport.dbo.opportunity

  67    llp\_alltrucksapprovedandaccepted                bit                Yes     Column llp\_alltrucksapprovedandaccepted from
                                                                                    ScaniaCRMExport.dbo.opportunity

  68    llp\_approvalstatus                              int                Yes     Column llp\_approvalstatus from
                                                                                    ScaniaCRMExport.dbo.opportunity

  69    llp\_assetprice                                  decimal            Yes     Column llp\_assetprice from
                                                                                    ScaniaCRMExport.dbo.opportunity

  70    llp\_assetprice\_base                            decimal            Yes     Column llp\_assetprice\_base from
                                                                                    ScaniaCRMExport.dbo.opportunity

  71    llp\_automaticallycreatedsfopp                   datetime           Yes     Column llp\_automaticallycreatedsfopp from
                                                                                    ScaniaCRMExport.dbo.opportunity

  72    llp\_automaticallycreatedsiopp                   datetime           Yes     Column llp\_automaticallycreatedsiopp from
                                                                                    ScaniaCRMExport.dbo.opportunity

  73    llp\_averageoverdueinlast2years                  decimal            Yes     Column llp\_averageoverdueinlast2years from
                                                                                    ScaniaCRMExport.dbo.opportunity

  74    llp\_bodybuildingcontractsigned                  bit                Yes     Column llp\_bodybuildingcontractsigned from
                                                                                    ScaniaCRMExport.dbo.opportunity

  75    llp\_bodybuildingcoordinatedby                   int                Yes     Column llp\_bodybuildingcoordinatedby from
                                                                                    ScaniaCRMExport.dbo.opportunity

  76    llp\_bodybuildinggeneralsupplierid               uniqueidentifier   Yes     Column llp\_bodybuildinggeneralsupplierid from
                                                                                    ScaniaCRMExport.dbo.opportunity

  77    llp\_bodybuildinggeneralsupplierid\_entitytype   nvarchar(512)      Yes     Column
                                                                                    llp\_bodybuildinggeneralsupplierid\_entitytype
                                                                                    from ScaniaCRMExport.dbo.opportunity

  78    llp\_bodybuildinggeneralsupplieridname           nvarchar(400)      Yes     Column llp\_bodybuildinggeneralsupplieridname
                                                                                    from ScaniaCRMExport.dbo.opportunity

  79    llp\_bodybuildinggeneralsupplieridyominame       nvarchar(400)      Yes     Column
                                                                                    llp\_bodybuildinggeneralsupplieridyominame from
                                                                                    ScaniaCRMExport.dbo.opportunity

  80    llp\_bodybuildinghandoverdate                    datetime           Yes     Column llp\_bodybuildinghandoverdate from
                                                                                    ScaniaCRMExport.dbo.opportunity

  81    llp\_bodywork                                    int                Yes     Column llp\_bodywork from
                                                                                    ScaniaCRMExport.dbo.opportunity

  82    llp\_buofvehicleid                               uniqueidentifier   Yes     Column llp\_buofvehicleid from
                                                                                    ScaniaCRMExport.dbo.opportunity

  83    llp\_buofvehicleid\_entitytype                   nvarchar(512)      Yes     Column llp\_buofvehicleid\_entitytype from
                                                                                    ScaniaCRMExport.dbo.opportunity

  84    llp\_buofvehicleidname                           nvarchar(640)      Yes     Column llp\_buofvehicleidname from
                                                                                    ScaniaCRMExport.dbo.opportunity

  85    llp\_cdd                                         datetime           Yes     Column llp\_cdd from
                                                                                    ScaniaCRMExport.dbo.opportunity

  86    llp\_checkedofcustomerneeds                      bit                Yes     Column llp\_checkedofcustomerneeds from
                                                                                    ScaniaCRMExport.dbo.opportunity

  87    llp\_competitors                                 int                Yes     Column llp\_competitors from
                                                                                    ScaniaCRMExport.dbo.opportunity

  88    llp\_competitorsinsuraceother                    nvarchar(800)      Yes     Column llp\_competitorsinsuraceother from
                                                                                    ScaniaCRMExport.dbo.opportunity

  89    llp\_competitorsinsurance                        int                Yes     Column llp\_competitorsinsurance from
                                                                                    ScaniaCRMExport.dbo.opportunity

  90    llp\_competitorsinsuranceselection               nvarchar(max)      Yes     Column llp\_competitorsinsuranceselection from
                                                                                    ScaniaCRMExport.dbo.opportunity

  91    llp\_competitorsleasingother                     nvarchar(800)      Yes     Column llp\_competitorsleasingother from
                                                                                    ScaniaCRMExport.dbo.opportunity

  92    llp\_competitorsselection                        nvarchar(max)      Yes     Column llp\_competitorsselection from
                                                                                    ScaniaCRMExport.dbo.opportunity

  93    llp\_contractlenght                              int                Yes     Column llp\_contractlenght from
                                                                                    ScaniaCRMExport.dbo.opportunity

  94    llp\_contractlengthmonth                         int                Yes     Column llp\_contractlengthmonth from
                                                                                    ScaniaCRMExport.dbo.opportunity

  95    llp\_contractsigned                              int                Yes     Column llp\_contractsigned from
                                                                                    ScaniaCRMExport.dbo.opportunity

  96    llp\_contractsignedby                            uniqueidentifier   Yes     Column llp\_contractsignedby from
                                                                                    ScaniaCRMExport.dbo.opportunity

  97    llp\_contractsignedby\_entitytype                nvarchar(512)      Yes     Column llp\_contractsignedby\_entitytype from
                                                                                    ScaniaCRMExport.dbo.opportunity

  98    llp\_contractsignedbyname                        nvarchar(640)      Yes     Column llp\_contractsignedbyname from
                                                                                    ScaniaCRMExport.dbo.opportunity

  99    llp\_contractsignedbyon                          datetime           Yes     Column llp\_contractsignedbyon from
                                                                                    ScaniaCRMExport.dbo.opportunity

  100   llp\_contractsignedbyyominame                    nvarchar(1800)     Yes     Column llp\_contractsignedbyyominame from
                                                                                    ScaniaCRMExport.dbo.opportunity

  101   llp\_contracttype                                int                Yes     Column llp\_contracttype from
                                                                                    ScaniaCRMExport.dbo.opportunity

  102   llp\_countofofferedtrucks                        int                Yes     Column llp\_countofofferedtrucks from
                                                                                    ScaniaCRMExport.dbo.opportunity

  103   llp\_countofofferedtrucks\_date                  datetime           Yes     Column llp\_countofofferedtrucks\_date from
                                                                                    ScaniaCRMExport.dbo.opportunity

  104   llp\_countofofferedtrucks\_state                 int                Yes     Column llp\_countofofferedtrucks\_state from
                                                                                    ScaniaCRMExport.dbo.opportunity

  105   llp\_countrieswerefilled                         bit                Yes     Column llp\_countrieswerefilled from
                                                                                    ScaniaCRMExport.dbo.opportunity

  106   llp\_createdonreport                             datetime           Yes     Column llp\_createdonreport from
                                                                                    ScaniaCRMExport.dbo.opportunity

  107   llp\_createsportoffer                            bit                Yes     Column llp\_createsportoffer from
                                                                                    ScaniaCRMExport.dbo.opportunity

  108   llp\_creditapplicationapproved                   bit                Yes     Column llp\_creditapplicationapproved from
                                                                                    ScaniaCRMExport.dbo.opportunity

  109   llp\_creditapplicationcreated                    bit                Yes     Column llp\_creditapplicationcreated from
                                                                                    ScaniaCRMExport.dbo.opportunity

  110   llp\_creditprecheckdone                          int                Yes     Column llp\_creditprecheckdone from
                                                                                    ScaniaCRMExport.dbo.opportunity

  111   llp\_currency                                    decimal            Yes     Column llp\_currency from
                                                                                    ScaniaCRMExport.dbo.opportunity

  112   llp\_currency\_base                              decimal            Yes     Column llp\_currency\_base from
                                                                                    ScaniaCRMExport.dbo.opportunity

  113   llp\_currentfleetmileage                         int                Yes     Column llp\_currentfleetmileage from
                                                                                    ScaniaCRMExport.dbo.opportunity

  114   llp\_currentfleetmileagekmyear                   int                Yes     Column llp\_currentfleetmileagekmyear from
                                                                                    ScaniaCRMExport.dbo.opportunity

  115   llp\_customeracceptedtheoffer                    bit                Yes     Column llp\_customeracceptedtheoffer from
                                                                                    ScaniaCRMExport.dbo.opportunity

  116   llp\_customerbillingaddress                      nvarchar(400)      Yes     Column llp\_customerbillingaddress from
                                                                                    ScaniaCRMExport.dbo.opportunity

  117   llp\_customeremail                               nvarchar(400)      Yes     Column llp\_customeremail from
                                                                                    ScaniaCRMExport.dbo.opportunity

  118   llp\_customername                                nvarchar(400)      Yes     Column llp\_customername from
                                                                                    ScaniaCRMExport.dbo.opportunity

  119   llp\_customerphone                               nvarchar(400)      Yes     Column llp\_customerphone from
                                                                                    ScaniaCRMExport.dbo.opportunity

  120   llp\_customerswerefilled                         bit                Yes     Column llp\_customerswerefilled from
                                                                                    ScaniaCRMExport.dbo.opportunity

  121   llp\_deliverycompleted                           bit                Yes     Column llp\_deliverycompleted from
                                                                                    ScaniaCRMExport.dbo.opportunity

  122   llp\_deliverydate                                datetime           Yes     Column llp\_deliverydate from
                                                                                    ScaniaCRMExport.dbo.opportunity

  123   llp\_dout                                        datetime           Yes     Column llp\_dout from
                                                                                    ScaniaCRMExport.dbo.opportunity

  124   llp\_downpayment                                 int                Yes     Column llp\_downpayment from
                                                                                    ScaniaCRMExport.dbo.opportunity

  125   llp\_dppercent                                   decimal            Yes     Column llp\_dppercent from
                                                                                    ScaniaCRMExport.dbo.opportunity

  126   llp\_estimatedbodybuildingcompletiondate         datetime           Yes     Column llp\_estimatedbodybuildingcompletiondate
                                                                                    from ScaniaCRMExport.dbo.opportunity

  127   llp\_estimateddeliverydate                       datetime           Yes     Column llp\_estimateddeliverydate from
                                                                                    ScaniaCRMExport.dbo.opportunity

  128   llp\_estimatedorderdate                          datetime           Yes     Column llp\_estimatedorderdate from
                                                                                    ScaniaCRMExport.dbo.opportunity

  129   llp\_externalfinancing                           bit                Yes     Column llp\_externalfinancing from
                                                                                    ScaniaCRMExport.dbo.opportunity

  130   llp\_financing2                                  int                Yes     Column llp\_financing2 from
                                                                                    ScaniaCRMExport.dbo.opportunity

  131   llp\_financingapproved                           int                Yes     Column llp\_financingapproved from
                                                                                    ScaniaCRMExport.dbo.opportunity

  132   llp\_financingconfirmed                          int                Yes     Column llp\_financingconfirmed from
                                                                                    ScaniaCRMExport.dbo.opportunity

  133   llp\_financinghidden                             bit                Yes     Column llp\_financinghidden from
                                                                                    ScaniaCRMExport.dbo.opportunity

  134   llp\_financingnoreasonother                      nvarchar(800)      Yes     Column llp\_financingnoreasonother from
                                                                                    ScaniaCRMExport.dbo.opportunity

  135   llp\_financingnothereason                        int                Yes     Column llp\_financingnothereason from
                                                                                    ScaniaCRMExport.dbo.opportunity

  136   llp\_financingopportunitycreated                 bit                Yes     Column llp\_financingopportunitycreated from
                                                                                    ScaniaCRMExport.dbo.opportunity

  137   llp\_gdprcheck                                   bit                Yes     Column llp\_gdprcheck from
                                                                                    ScaniaCRMExport.dbo.opportunity

  138   llp\_htmlspread                                  nvarchar(max)      Yes     Column llp\_htmlspread from
                                                                                    ScaniaCRMExport.dbo.opportunity

  139   llp\_indicativeofferaccepted                     bit                Yes     Column llp\_indicativeofferaccepted from
                                                                                    ScaniaCRMExport.dbo.opportunity

  140   llp\_indicativeofferwassaved                     bit                Yes     Column llp\_indicativeofferwassaved from
                                                                                    ScaniaCRMExport.dbo.opportunity

  141   llp\_informationdirectlyfromcustomer             bit                Yes     Column llp\_informationdirectlyfromcustomer from
                                                                                    ScaniaCRMExport.dbo.opportunity

  142   llp\_informationfromjusticecz                    bit                Yes     Column llp\_informationfromjusticecz from
                                                                                    ScaniaCRMExport.dbo.opportunity

  143   llp\_insurance2                                  int                Yes     Column llp\_insurance2 from
                                                                                    ScaniaCRMExport.dbo.opportunity

  144   llp\_insurancehidden                             bit                Yes     Column llp\_insurancehidden from
                                                                                    ScaniaCRMExport.dbo.opportunity

  145   llp\_insuranceprice                              decimal            Yes     Column llp\_insuranceprice from
                                                                                    ScaniaCRMExport.dbo.opportunity

  146   llp\_insuranceprice\_base                        decimal            Yes     Column llp\_insuranceprice\_base from
                                                                                    ScaniaCRMExport.dbo.opportunity

  147   llp\_insuranceproductsselection                  nvarchar(max)      Yes     Column llp\_insuranceproductsselection from
                                                                                    ScaniaCRMExport.dbo.opportunity

  148   llp\_insuranceproductswereselected               bit                Yes     Column llp\_insuranceproductswereselected from
                                                                                    ScaniaCRMExport.dbo.opportunity

  149   llp\_insurenceoffersend                          bit                Yes     Column llp\_insurenceoffersend from
                                                                                    ScaniaCRMExport.dbo.opportunity

  150   llp\_insurersselection                           nvarchar(max)      Yes     Column llp\_insurersselection from
                                                                                    ScaniaCRMExport.dbo.opportunity

  151   llp\_insurerswereselected                        bit                Yes     Column llp\_insurerswereselected from
                                                                                    ScaniaCRMExport.dbo.opportunity

  152   llp\_integrationsportguid                        nvarchar(400)      Yes     Column llp\_integrationsportguid from
                                                                                    ScaniaCRMExport.dbo.opportunity

  153   llp\_km                                          int                Yes     Column llp\_km from
                                                                                    ScaniaCRMExport.dbo.opportunity

  154   llp\_knownrivaloffer                             bit                Yes     Column llp\_knownrivaloffer from
                                                                                    ScaniaCRMExport.dbo.opportunity

  155   llp\_leasingasset                                int                Yes     Column llp\_leasingasset from
                                                                                    ScaniaCRMExport.dbo.opportunity

  156   llp\_lockguid                                    nvarchar(400)      Yes     Column llp\_lockguid from
                                                                                    ScaniaCRMExport.dbo.opportunity

  157   llp\_lossratiopercent                            decimal            Yes     Column llp\_lossratiopercent from
                                                                                    ScaniaCRMExport.dbo.opportunity

  158   llp\_margin                                      decimal            Yes     Column llp\_margin from
                                                                                    ScaniaCRMExport.dbo.opportunity

  159   llp\_maxage                                      int                Yes     Column llp\_maxage from
                                                                                    ScaniaCRMExport.dbo.opportunity

  160   llp\_maxmileage                                  int                Yes     Column llp\_maxmileage from
                                                                                    ScaniaCRMExport.dbo.opportunity

  161   llp\_maxprice                                    decimal            Yes     Column llp\_maxprice from
                                                                                    ScaniaCRMExport.dbo.opportunity

  162   llp\_maxprice\_base                              decimal            Yes     Column llp\_maxprice\_base from
                                                                                    ScaniaCRMExport.dbo.opportunity

  163   llp\_meetingwithbodybuilder                      bit                Yes     Column llp\_meetingwithbodybuilder from
                                                                                    ScaniaCRMExport.dbo.opportunity

  164   llp\_netsuitechange                              int                Yes     Column llp\_netsuitechange from
                                                                                    ScaniaCRMExport.dbo.opportunity

  165   llp\_newpurchasemileagekmyear                    int                Yes     Column llp\_newpurchasemileagekmyear from
                                                                                    ScaniaCRMExport.dbo.opportunity

  166   llp\_newpurchusemileage                          int                Yes     Column llp\_newpurchusemileage from
                                                                                    ScaniaCRMExport.dbo.opportunity

  167   llp\_notifydrivecoach                            bit                Yes     Column llp\_notifydrivecoach from
                                                                                    ScaniaCRMExport.dbo.opportunity

  168   llp\_numberofitemsofobjectspecification          int                Yes     Column llp\_numberofitemsofobjectspecification
                                                                                    from ScaniaCRMExport.dbo.opportunity

  169   llp\_numberofitemsofobjectspecification\_date    datetime           Yes     Column
                                                                                    llp\_numberofitemsofobjectspecification\_date
                                                                                    from ScaniaCRMExport.dbo.opportunity

  170   llp\_numberofitemsofobjectspecification\_state   int                Yes     Column
                                                                                    llp\_numberofitemsofobjectspecification\_state
                                                                                    from ScaniaCRMExport.dbo.opportunity

  171   llp\_numberoftrucks                              int                Yes     Column llp\_numberoftrucks from
                                                                                    ScaniaCRMExport.dbo.opportunity

  172   llp\_numberoftrucksinfleet                       int                Yes     Column llp\_numberoftrucksinfleet from
                                                                                    ScaniaCRMExport.dbo.opportunity

  173   llp\_objectspecificationcompleted                bit                Yes     Column llp\_objectspecificationcompleted from
                                                                                    ScaniaCRMExport.dbo.opportunity

  174   llp\_offeraccepted                               bit                Yes     Column llp\_offeraccepted from
                                                                                    ScaniaCRMExport.dbo.opportunity

  175   llp\_offeracceptedbycustomer                     bit                Yes     Column llp\_offeracceptedbycustomer from
                                                                                    ScaniaCRMExport.dbo.opportunity

  176   llp\_opportunitycountries\_count                 int                Yes     Column llp\_opportunitycountries\_count from
                                                                                    ScaniaCRMExport.dbo.opportunity

  177   llp\_opportunitycountries\_weightsum             decimal            Yes     Column llp\_opportunitycountries\_weightsum from
                                                                                    ScaniaCRMExport.dbo.opportunity

  178   llp\_opportunitycustomer\_count                  int                Yes     Column llp\_opportunitycustomer\_count from
                                                                                    ScaniaCRMExport.dbo.opportunity

  179   llp\_opportunitycustomer\_weightsum              decimal            Yes     Column llp\_opportunitycustomer\_weightsum from
                                                                                    ScaniaCRMExport.dbo.opportunity

  180   llp\_opportunityforfinancingwaslost              bit                Yes     Column llp\_opportunityforfinancingwaslost from
                                                                                    ScaniaCRMExport.dbo.opportunity

  181   llp\_opportunitynumber                           nvarchar(400)      Yes     Column llp\_opportunitynumber from
                                                                                    ScaniaCRMExport.dbo.opportunity

  182   llp\_opportunitypreferableinsurer\_count         int                Yes     Column llp\_opportunitypreferableinsurer\_count
                                                                                    from ScaniaCRMExport.dbo.opportunity

  183   llp\_opportunitytype                             int                Yes     Column llp\_opportunitytype from
                                                                                    ScaniaCRMExport.dbo.opportunity

  184   llp\_opportunitytypeofinsurance\_count           int                Yes     Column llp\_opportunitytypeofinsurance\_count
                                                                                    from ScaniaCRMExport.dbo.opportunity

  185   llp\_parentalbuid                                uniqueidentifier   Yes     Column llp\_parentalbuid from
                                                                                    ScaniaCRMExport.dbo.opportunity

  186   llp\_parentalbuid\_entitytype                    nvarchar(512)      Yes     Column llp\_parentalbuid\_entitytype from
                                                                                    ScaniaCRMExport.dbo.opportunity

  187   llp\_parentalbuidname                            nvarchar(640)      Yes     Column llp\_parentalbuidname from
                                                                                    ScaniaCRMExport.dbo.opportunity

  188   llp\_pdicomplete                                 bit                Yes     Column llp\_pdicomplete from
                                                                                    ScaniaCRMExport.dbo.opportunity

  189   llp\_peakinlastyear                              decimal            Yes     Column llp\_peakinlastyear from
                                                                                    ScaniaCRMExport.dbo.opportunity

  190   llp\_preferableinsurerid                         uniqueidentifier   Yes     Column llp\_preferableinsurerid from
                                                                                    ScaniaCRMExport.dbo.opportunity

  191   llp\_preferableinsurerid\_entitytype             nvarchar(512)      Yes     Column llp\_preferableinsurerid\_entitytype from
                                                                                    ScaniaCRMExport.dbo.opportunity

  192   llp\_preferableinsureridname                     nvarchar(400)      Yes     Column llp\_preferableinsureridname from
                                                                                    ScaniaCRMExport.dbo.opportunity

  193   llp\_preferedfinancialproduct                    int                Yes     Column llp\_preferedfinancialproduct from
                                                                                    ScaniaCRMExport.dbo.opportunity

  194   llp\_primaryquoteid                              uniqueidentifier   Yes     Column llp\_primaryquoteid from
                                                                                    ScaniaCRMExport.dbo.opportunity

  195   llp\_primaryquoteid\_entitytype                  nvarchar(512)      Yes     Column llp\_primaryquoteid\_entitytype from
                                                                                    ScaniaCRMExport.dbo.opportunity

  196   llp\_primaryquoteidname                          nvarchar(400)      Yes     Column llp\_primaryquoteidname from
                                                                                    ScaniaCRMExport.dbo.opportunity

  197   llp\_proposalsentdate                            datetime           Yes     Column llp\_proposalsentdate from
                                                                                    ScaniaCRMExport.dbo.opportunity

  198   llp\_proposedprice                               decimal            Yes     Column llp\_proposedprice from
                                                                                    ScaniaCRMExport.dbo.opportunity

  199   llp\_proposedprice\_base                         decimal            Yes     Column llp\_proposedprice\_base from
                                                                                    ScaniaCRMExport.dbo.opportunity

  200   llp\_recordapproved                              int                Yes     Column llp\_recordapproved from
                                                                                    ScaniaCRMExport.dbo.opportunity

  201   llp\_regno                                       nvarchar(400)      Yes     Column llp\_regno from
                                                                                    ScaniaCRMExport.dbo.opportunity

  202   llp\_remark                                      nvarchar(400)      Yes     Column llp\_remark from
                                                                                    ScaniaCRMExport.dbo.opportunity

  203   llp\_reservevehicle                              bit                Yes     Column llp\_reservevehicle from
                                                                                    ScaniaCRMExport.dbo.opportunity

  204   llp\_service                                     int                Yes     Column llp\_service from
                                                                                    ScaniaCRMExport.dbo.opportunity

  205   llp\_servicesactivated                           bit                Yes     Column llp\_servicesactivated from
                                                                                    ScaniaCRMExport.dbo.opportunity

  206   llp\_sfcategory                                  int                Yes     Column llp\_sfcategory from
                                                                                    ScaniaCRMExport.dbo.opportunity

  207   llp\_sourceopportunityid                         uniqueidentifier   Yes     Column llp\_sourceopportunityid from
                                                                                    ScaniaCRMExport.dbo.opportunity

  208   llp\_sourceopportunityid\_entitytype             nvarchar(512)      Yes     Column llp\_sourceopportunityid\_entitytype from
                                                                                    ScaniaCRMExport.dbo.opportunity

  209   llp\_sourceopportunityidname                     nvarchar(400)      Yes     Column llp\_sourceopportunityidname from
                                                                                    ScaniaCRMExport.dbo.opportunity

  210   llp\_spreadapplicationapproved                   bit                Yes     Column llp\_spreadapplicationapproved from
                                                                                    ScaniaCRMExport.dbo.opportunity

  211   llp\_spreadapplicationmarginreason               int                Yes     Column llp\_spreadapplicationmarginreason from
                                                                                    ScaniaCRMExport.dbo.opportunity

  212   llp\_subjecttbfinanced                           nvarchar(400)      Yes     Column llp\_subjecttbfinanced from
                                                                                    ScaniaCRMExport.dbo.opportunity

  213   llp\_tradein                                     int                Yes     Column llp\_tradein from
                                                                                    ScaniaCRMExport.dbo.opportunity

  214   llp\_tradeinrequestcompleted                     bit                Yes     Column llp\_tradeinrequestcompleted from
                                                                                    ScaniaCRMExport.dbo.opportunity

  215   llp\_trucktype                                   int                Yes     Column llp\_trucktype from
                                                                                    ScaniaCRMExport.dbo.opportunity

  216   llp\_typeofinsuranceproduct                      bit                Yes     Column llp\_typeofinsuranceproduct from
                                                                                    ScaniaCRMExport.dbo.opportunity

  217   llp\_typeoftransport                             int                Yes     Column llp\_typeoftransport from
                                                                                    ScaniaCRMExport.dbo.opportunity

  218   llp\_typeoftransportselection                    nvarchar(max)      Yes     Column llp\_typeoftransportselection from
                                                                                    ScaniaCRMExport.dbo.opportunity

  219   llp\_urljusticecz                                nvarchar(400)      Yes     Column llp\_urljusticecz from
                                                                                    ScaniaCRMExport.dbo.opportunity

  220   llp\_utreservationapprovalrequired               bit                Yes     Column llp\_utreservationapprovalrequired from
                                                                                    ScaniaCRMExport.dbo.opportunity

  221   llp\_utreservationapproverhiddenid               uniqueidentifier   Yes     Column llp\_utreservationapproverhiddenid from
                                                                                    ScaniaCRMExport.dbo.opportunity

  222   llp\_utreservationapproverhiddenid\_entitytype   nvarchar(512)      Yes     Column
                                                                                    llp\_utreservationapproverhiddenid\_entitytype
                                                                                    from ScaniaCRMExport.dbo.opportunity

  223   llp\_utreservationapproverhiddenidname           nvarchar(800)      Yes     Column llp\_utreservationapproverhiddenidname
                                                                                    from ScaniaCRMExport.dbo.opportunity

  224   llp\_utreservationapproverhiddenidyominame       nvarchar(800)      Yes     Column
                                                                                    llp\_utreservationapproverhiddenidyominame from
                                                                                    ScaniaCRMExport.dbo.opportunity

  225   llp\_utsalespersonid                             uniqueidentifier   Yes     Column llp\_utsalespersonid from
                                                                                    ScaniaCRMExport.dbo.opportunity

  226   llp\_utsalespersonid\_entitytype                 nvarchar(512)      Yes     Column llp\_utsalespersonid\_entitytype from
                                                                                    ScaniaCRMExport.dbo.opportunity

  227   llp\_utsalespersonidname                         nvarchar(800)      Yes     Column llp\_utsalespersonidname from
                                                                                    ScaniaCRMExport.dbo.opportunity

  228   llp\_utsalespersonidyominame                     nvarchar(800)      Yes     Column llp\_utsalespersonidyominame from
                                                                                    ScaniaCRMExport.dbo.opportunity

  229   llp\_vehicleid                                   uniqueidentifier   Yes     Column llp\_vehicleid from
                                                                                    ScaniaCRMExport.dbo.opportunity

  230   llp\_vehicleid\_entitytype                       nvarchar(512)      Yes     Column llp\_vehicleid\_entitytype from
                                                                                    ScaniaCRMExport.dbo.opportunity

  231   llp\_vehicleidname                               nvarchar(400)      Yes     Column llp\_vehicleidname from
                                                                                    ScaniaCRMExport.dbo.opportunity

  232   llp\_vehicleprice                                decimal            Yes     Column llp\_vehicleprice from
                                                                                    ScaniaCRMExport.dbo.opportunity

  233   llp\_vehicleprice\_base                          decimal            Yes     Column llp\_vehicleprice\_base from
                                                                                    ScaniaCRMExport.dbo.opportunity

  234   llp\_vehicleregistrationnumber                   nvarchar(400)      Yes     Column llp\_vehicleregistrationnumber from
                                                                                    ScaniaCRMExport.dbo.opportunity

  235   llp\_vin                                         nvarchar(400)      Yes     Column llp\_vin from
                                                                                    ScaniaCRMExport.dbo.opportunity

  236   llp\_virtualaccount                              bit                Yes     Column llp\_virtualaccount from
                                                                                    ScaniaCRMExport.dbo.opportunity

  237   llp\_weightsumcountriesissue                     nvarchar(400)      Yes     Column llp\_weightsumcountriesissue from
                                                                                    ScaniaCRMExport.dbo.opportunity

  238   llp\_weightsumcustomersissue                     nvarchar(400)      Yes     Column llp\_weightsumcustomersissue from
                                                                                    ScaniaCRMExport.dbo.opportunity

  239   modifiedby                                       uniqueidentifier   Yes     Column modifiedby from
                                                                                    ScaniaCRMExport.dbo.opportunity

  240   modifiedby\_entitytype                           nvarchar(512)      Yes     Column modifiedby\_entitytype from
                                                                                    ScaniaCRMExport.dbo.opportunity

  241   modifiedbyname                                   nvarchar(400)      Yes     Column modifiedbyname from
                                                                                    ScaniaCRMExport.dbo.opportunity

  242   modifiedbyyominame                               nvarchar(400)      Yes     Column modifiedbyyominame from
                                                                                    ScaniaCRMExport.dbo.opportunity

  243   modifiedon                                       datetime           Yes     Column modifiedon from
                                                                                    ScaniaCRMExport.dbo.opportunity

  244   modifiedonbehalfby                               uniqueidentifier   Yes     Column modifiedonbehalfby from
                                                                                    ScaniaCRMExport.dbo.opportunity

  245   modifiedonbehalfby\_entitytype                   nvarchar(512)      Yes     Column modifiedonbehalfby\_entitytype from
                                                                                    ScaniaCRMExport.dbo.opportunity

  246   modifiedonbehalfbyname                           nvarchar(400)      Yes     Column modifiedonbehalfbyname from
                                                                                    ScaniaCRMExport.dbo.opportunity

  247   modifiedonbehalfbyyominame                       nvarchar(400)      Yes     Column modifiedonbehalfbyyominame from
                                                                                    ScaniaCRMExport.dbo.opportunity

  248   msdyn\_forecastcategory                          int                Yes     Column msdyn\_forecastcategory from
                                                                                    ScaniaCRMExport.dbo.opportunity

  249   name                                             nvarchar(1200)     Yes     Column name from ScaniaCRMExport.dbo.opportunity

  250   need                                             int                Yes     Column need from ScaniaCRMExport.dbo.opportunity

  251   onholdtime                                       int                Yes     Column onholdtime from
                                                                                    ScaniaCRMExport.dbo.opportunity

  252   opportunityid                                    uniqueidentifier   Yes     Column opportunityid from
                                                                                    ScaniaCRMExport.dbo.opportunity

  253   opportunityratingcode                            int                Yes     Column opportunityratingcode from
                                                                                    ScaniaCRMExport.dbo.opportunity

  254   originatingleadid                                uniqueidentifier   Yes     Column originatingleadid from
                                                                                    ScaniaCRMExport.dbo.opportunity

  255   originatingleadid\_entitytype                    nvarchar(512)      Yes     Column originatingleadid\_entitytype from
                                                                                    ScaniaCRMExport.dbo.opportunity

  256   originatingleadidname                            nvarchar(400)      Yes     Column originatingleadidname from
                                                                                    ScaniaCRMExport.dbo.opportunity

  257   originatingleadidyominame                        nvarchar(400)      Yes     Column originatingleadidyominame from
                                                                                    ScaniaCRMExport.dbo.opportunity

  258   overriddencreatedon                              datetime           Yes     Column overriddencreatedon from
                                                                                    ScaniaCRMExport.dbo.opportunity

  259   ownerid                                          uniqueidentifier   Yes     Column ownerid from
                                                                                    ScaniaCRMExport.dbo.opportunity

  260   ownerid\_entitytype                              nvarchar(512)      Yes     Column ownerid\_entitytype from
                                                                                    ScaniaCRMExport.dbo.opportunity

  261   owneridname                                      nvarchar(400)      Yes     Column owneridname from
                                                                                    ScaniaCRMExport.dbo.opportunity

  262   owneridtype                                      nvarchar(max)      Yes     Column owneridtype from
                                                                                    ScaniaCRMExport.dbo.opportunity

  263   owneridyominame                                  nvarchar(400)      Yes     Column owneridyominame from
                                                                                    ScaniaCRMExport.dbo.opportunity

  264   owningbusinessunit                               uniqueidentifier   Yes     Column owningbusinessunit from
                                                                                    ScaniaCRMExport.dbo.opportunity

  265   owningbusinessunit\_entitytype                   nvarchar(512)      Yes     Column owningbusinessunit\_entitytype from
                                                                                    ScaniaCRMExport.dbo.opportunity

  266   owningteam                                       uniqueidentifier   Yes     Column owningteam from
                                                                                    ScaniaCRMExport.dbo.opportunity

  267   owningteam\_entitytype                           nvarchar(512)      Yes     Column owningteam\_entitytype from
                                                                                    ScaniaCRMExport.dbo.opportunity

  268   owninguser                                       uniqueidentifier   Yes     Column owninguser from
                                                                                    ScaniaCRMExport.dbo.opportunity

  269   owninguser\_entitytype                           nvarchar(512)      Yes     Column owninguser\_entitytype from
                                                                                    ScaniaCRMExport.dbo.opportunity

  270   parentaccountid                                  uniqueidentifier   Yes     Column parentaccountid from
                                                                                    ScaniaCRMExport.dbo.opportunity

  271   parentaccountid\_entitytype                      nvarchar(512)      Yes     Column parentaccountid\_entitytype from
                                                                                    ScaniaCRMExport.dbo.opportunity

  272   parentaccountidname                              nvarchar(400)      Yes     Column parentaccountidname from
                                                                                    ScaniaCRMExport.dbo.opportunity

  273   parentaccountidyominame                          nvarchar(400)      Yes     Column parentaccountidyominame from
                                                                                    ScaniaCRMExport.dbo.opportunity

  274   parentcontactid                                  uniqueidentifier   Yes     Column parentcontactid from
                                                                                    ScaniaCRMExport.dbo.opportunity

  275   parentcontactid\_entitytype                      nvarchar(512)      Yes     Column parentcontactid\_entitytype from
                                                                                    ScaniaCRMExport.dbo.opportunity

  276   parentcontactidname                              nvarchar(400)      Yes     Column parentcontactidname from
                                                                                    ScaniaCRMExport.dbo.opportunity

  277   parentcontactidyominame                          nvarchar(400)      Yes     Column parentcontactidyominame from
                                                                                    ScaniaCRMExport.dbo.opportunity

  278   participatesinworkflow                           bit                Yes     Column participatesinworkflow from
                                                                                    ScaniaCRMExport.dbo.opportunity

  279   presentfinalproposal                             bit                Yes     Column presentfinalproposal from
                                                                                    ScaniaCRMExport.dbo.opportunity

  280   presentproposal                                  bit                Yes     Column presentproposal from
                                                                                    ScaniaCRMExport.dbo.opportunity

  281   pricelevelid                                     uniqueidentifier   Yes     Column pricelevelid from
                                                                                    ScaniaCRMExport.dbo.opportunity

  282   pricelevelid\_entitytype                         nvarchar(512)      Yes     Column pricelevelid\_entitytype from
                                                                                    ScaniaCRMExport.dbo.opportunity

  283   pricelevelidname                                 nvarchar(400)      Yes     Column pricelevelidname from
                                                                                    ScaniaCRMExport.dbo.opportunity

  284   pricingerrorcode                                 int                Yes     Column pricingerrorcode from
                                                                                    ScaniaCRMExport.dbo.opportunity

  285   prioritycode                                     int                Yes     Column prioritycode from
                                                                                    ScaniaCRMExport.dbo.opportunity

  286   processid                                        uniqueidentifier   Yes     Column processid from
                                                                                    ScaniaCRMExport.dbo.opportunity

  287   proposedsolution                                 nvarchar(max)      Yes     Column proposedsolution from
                                                                                    ScaniaCRMExport.dbo.opportunity

  288   purchaseprocess                                  int                Yes     Column purchaseprocess from
                                                                                    ScaniaCRMExport.dbo.opportunity

  289   purchasetimeframe                                int                Yes     Column purchasetimeframe from
                                                                                    ScaniaCRMExport.dbo.opportunity

  290   pursuitdecision                                  bit                Yes     Column pursuitdecision from
                                                                                    ScaniaCRMExport.dbo.opportunity

  291   qualificationcomments                            nvarchar(max)      Yes     Column qualificationcomments from
                                                                                    ScaniaCRMExport.dbo.opportunity

  292   quotecomments                                    nvarchar(max)      Yes     Column quotecomments from
                                                                                    ScaniaCRMExport.dbo.opportunity

  293   resolvefeedback                                  bit                Yes     Column resolvefeedback from
                                                                                    ScaniaCRMExport.dbo.opportunity

  294   salesstage                                       int                Yes     Column salesstage from
                                                                                    ScaniaCRMExport.dbo.opportunity

  295   salesstagecode                                   int                Yes     Column salesstagecode from
                                                                                    ScaniaCRMExport.dbo.opportunity

  296   schedulefollowup\_prospect                       datetime           Yes     Column schedulefollowup\_prospect from
                                                                                    ScaniaCRMExport.dbo.opportunity

  297   schedulefollowup\_qualify                        datetime           Yes     Column schedulefollowup\_qualify from
                                                                                    ScaniaCRMExport.dbo.opportunity

  298   scheduleproposalmeeting                          datetime           Yes     Column scheduleproposalmeeting from
                                                                                    ScaniaCRMExport.dbo.opportunity

  299   sendthankyounote                                 bit                Yes     Column sendthankyounote from
                                                                                    ScaniaCRMExport.dbo.opportunity

  300   SinkCreatedOn                                    datetime           Yes     Column SinkCreatedOn from
                                                                                    ScaniaCRMExport.dbo.opportunity

  301   SinkModifiedOn                                   datetime           Yes     Column SinkModifiedOn from
                                                                                    ScaniaCRMExport.dbo.opportunity

  302   slaid                                            uniqueidentifier   Yes     Column slaid from
                                                                                    ScaniaCRMExport.dbo.opportunity

  303   slaid\_entitytype                                nvarchar(512)      Yes     Column slaid\_entitytype from
                                                                                    ScaniaCRMExport.dbo.opportunity

  304   slainvokedid                                     uniqueidentifier   Yes     Column slainvokedid from
                                                                                    ScaniaCRMExport.dbo.opportunity

  305   slainvokedid\_entitytype                         nvarchar(512)      Yes     Column slainvokedid\_entitytype from
                                                                                    ScaniaCRMExport.dbo.opportunity

  306   slainvokedidname                                 nvarchar(400)      Yes     Column slainvokedidname from
                                                                                    ScaniaCRMExport.dbo.opportunity

  307   slaname                                          nvarchar(400)      Yes     Column slaname from
                                                                                    ScaniaCRMExport.dbo.opportunity

  308   stageid                                          uniqueidentifier   Yes     Column stageid from
                                                                                    ScaniaCRMExport.dbo.opportunity

  309   statecode                                        int                Yes     Column statecode from
                                                                                    ScaniaCRMExport.dbo.opportunity

  310   statuscode                                       int                Yes     Column statuscode from
                                                                                    ScaniaCRMExport.dbo.opportunity

  311   stepid                                           uniqueidentifier   Yes     Column stepid from
                                                                                    ScaniaCRMExport.dbo.opportunity

  312   stepname                                         nvarchar(800)      Yes     Column stepname from
                                                                                    ScaniaCRMExport.dbo.opportunity

  313   teamsfollowed                                    int                Yes     Column teamsfollowed from
                                                                                    ScaniaCRMExport.dbo.opportunity

  314   timeline                                         int                Yes     Column timeline from
                                                                                    ScaniaCRMExport.dbo.opportunity

  315   timespentbymeonemailandmeetings                  nvarchar(max)      Yes     Column timespentbymeonemailandmeetings from
                                                                                    ScaniaCRMExport.dbo.opportunity

  316   timezoneruleversionnumber                        int                Yes     Column timezoneruleversionnumber from
                                                                                    ScaniaCRMExport.dbo.opportunity

  317   totalamount                                      decimal            Yes     Column totalamount from
                                                                                    ScaniaCRMExport.dbo.opportunity

  318   totalamount\_base                                decimal            Yes     Column totalamount\_base from
                                                                                    ScaniaCRMExport.dbo.opportunity

  319   totalamountlessfreight                           decimal            Yes     Column totalamountlessfreight from
                                                                                    ScaniaCRMExport.dbo.opportunity

  320   totalamountlessfreight\_base                     decimal            Yes     Column totalamountlessfreight\_base from
                                                                                    ScaniaCRMExport.dbo.opportunity

  321   totaldiscountamount                              decimal            Yes     Column totaldiscountamount from
                                                                                    ScaniaCRMExport.dbo.opportunity

  322   totaldiscountamount\_base                        decimal            Yes     Column totaldiscountamount\_base from
                                                                                    ScaniaCRMExport.dbo.opportunity

  323   totallineitemamount                              decimal            Yes     Column totallineitemamount from
                                                                                    ScaniaCRMExport.dbo.opportunity

  324   totallineitemamount\_base                        decimal            Yes     Column totallineitemamount\_base from
                                                                                    ScaniaCRMExport.dbo.opportunity

  325   totallineitemdiscountamount                      decimal            Yes     Column totallineitemdiscountamount from
                                                                                    ScaniaCRMExport.dbo.opportunity

  326   totallineitemdiscountamount\_base                decimal            Yes     Column totallineitemdiscountamount\_base from
                                                                                    ScaniaCRMExport.dbo.opportunity

  327   totaltax                                         decimal            Yes     Column totaltax from
                                                                                    ScaniaCRMExport.dbo.opportunity

  328   totaltax\_base                                   decimal            Yes     Column totaltax\_base from
                                                                                    ScaniaCRMExport.dbo.opportunity

  329   transactioncurrencyid                            uniqueidentifier   Yes     Column transactioncurrencyid from
                                                                                    ScaniaCRMExport.dbo.opportunity

  330   transactioncurrencyid\_entitytype                nvarchar(512)      Yes     Column transactioncurrencyid\_entitytype from
                                                                                    ScaniaCRMExport.dbo.opportunity

  331   transactioncurrencyidname                        nvarchar(400)      Yes     Column transactioncurrencyidname from
                                                                                    ScaniaCRMExport.dbo.opportunity

  332   traversedpath                                    nvarchar(max)      Yes     Column traversedpath from
                                                                                    ScaniaCRMExport.dbo.opportunity

  333   utcconversiontimezonecode                        int                Yes     Column utcconversiontimezonecode from
                                                                                    ScaniaCRMExport.dbo.opportunity

  334   versionnumber                                    bigint             Yes     Column versionnumber from
                                                                                    ScaniaCRMExport.dbo.opportunity

  335   wa\_brandid                                      uniqueidentifier   Yes     Column wa\_brandid from
                                                                                    ScaniaCRMExport.dbo.opportunity

  336   wa\_brandid\_entitytype                          nvarchar(512)      Yes     Column wa\_brandid\_entitytype from
                                                                                    ScaniaCRMExport.dbo.opportunity

  337   wa\_brandidname                                  nvarchar(400)      Yes     Column wa\_brandidname from
                                                                                    ScaniaCRMExport.dbo.opportunity

  338   wa\_externalid                                   nvarchar(400)      Yes     Column wa\_externalid from
                                                                                    ScaniaCRMExport.dbo.opportunity

  339   wa\_opportunitygroup                             uniqueidentifier   Yes     Column wa\_opportunitygroup from
                                                                                    ScaniaCRMExport.dbo.opportunity

  340   wa\_opportunitygroup\_entitytype                 nvarchar(512)      Yes     Column wa\_opportunitygroup\_entitytype from
                                                                                    ScaniaCRMExport.dbo.opportunity

  341   wa\_opportunitygroupname                         nvarchar(400)      Yes     Column wa\_opportunitygroupname from
                                                                                    ScaniaCRMExport.dbo.opportunity

  342   wa\_opportunitysourceid                          uniqueidentifier   Yes     Column wa\_opportunitysourceid from
                                                                                    ScaniaCRMExport.dbo.opportunity

  343   wa\_opportunitysourceid\_entitytype              nvarchar(512)      Yes     Column wa\_opportunitysourceid\_entitytype from
                                                                                    ScaniaCRMExport.dbo.opportunity

  344   wa\_opportunitysourceidname                      nvarchar(400)      Yes     Column wa\_opportunitysourceidname from
                                                                                    ScaniaCRMExport.dbo.opportunity

  345   wa\_productid                                    uniqueidentifier   Yes     Column wa\_productid from
                                                                                    ScaniaCRMExport.dbo.opportunity

  346   wa\_productid\_entitytype                        nvarchar(512)      Yes     Column wa\_productid\_entitytype from
                                                                                    ScaniaCRMExport.dbo.opportunity

  347   wa\_productidname                                nvarchar(400)      Yes     Column wa\_productidname from
                                                                                    ScaniaCRMExport.dbo.opportunity

  348   DataSourceId                                     int                Yes     Id of the data source the row comes from

  349   ThreadLogId                                      int                Yes     Id of ThreadLog which inserted the row
  ----------------------------------------------------------------------------------------------------------------------------------

\[Back to table list\]\[listoftables\]
