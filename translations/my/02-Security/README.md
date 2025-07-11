<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "c69f9df7f3215dac8d056020539bac36",
  "translation_date": "2025-07-04T19:24:44+00:00",
  "source_file": "02-Security/README.md",
  "language_code": "my"
}
-->
# လုံခြုံရေးအကောင်းဆုံးလေ့လာမှုများ

Model Context Protocol (MCP) ကို အသုံးပြုခြင်းဖြင့် AI အခြေပြု အက်ပလီကေးရှင်းများတွင် အင်အားကြီးသော စွမ်းဆောင်ရည်အသစ်များရရှိနိုင်သော်လည်း၊ ရိုးရာဆော့ဖ်ဝဲလ်အန္တရာယ်များထက် ပိုမိုထူးခြားသော လုံခြုံရေး စိန်ခေါ်မှုများလည်း ဖြစ်ပေါ်လာသည်။ လုံခြုံရေးကုဒ်ရေးခြင်း၊ အနည်းဆုံးခွင့်ပြုချက်၊ နှင့် ပစ္စည်းလမ်းကြောင်းလုံခြုံရေးကဲ့သို့ ရှိပြီးသား စိုးရိမ်ချက်များအပြင် MCP နှင့် AI အလုပ်များတွင် prompt injection, tool poisoning, နှင့် dynamic tool modification ကဲ့သို့သော အန္တရာယ်အသစ်များလည်း ရှိသည်။ ဤအန္တရာယ်များကို မှန်ကန်စွာ စီမံမထားပါက ဒေတာထွက်ပေါက်ခြင်း၊ ကိုယ်ရေးကိုယ်တာ လုံခြုံမှုချိုးဖောက်ခြင်း၊ နှင့် မမျှော်လင့်ထားသော စနစ်အပြုအမူများ ဖြစ်ပေါ်နိုင်သည်။

ဤသင်ခန်းစာတွင် MCP နှင့်ဆက်စပ်သော အရေးကြီးသော လုံခြုံရေးအန္တရာယ်များ—အထူးသဖြင့် အတည်ပြုခြင်း၊ ခွင့်ပြုချက်၊ အလွန်အကျွံခွင့်ပြုချက်များ၊ အကြောင်းမပြောသော prompt injection နှင့် ပစ္စည်းလမ်းကြောင်း အားနည်းချက်များကို လေ့လာပြီး၊ ထိုအန္တရာယ်များကို လျော့နည်းစေရန် လုပ်ဆောင်နိုင်သော ထိန်းချုပ်မှုများနှင့် အကောင်းဆုံးလေ့လာမှုများကို ပေးအပ်ပါသည်။ ထို့အပြင် Microsoft ၏ Prompt Shields, Azure Content Safety, နှင့် GitHub Advanced Security ကဲ့သို့သော ဖြေရှင်းချက်များကို အသုံးပြု၍ MCP ကို ပိုမိုခိုင်မာစေရန်လည်း သင်ယူနိုင်ပါသည်။ ဤထိန်းချုပ်မှုများကို နားလည်ပြီး အသုံးချခြင်းဖြင့် လုံခြုံရေးချိုးဖောက်မှု ဖြစ်ပေါ်နိုင်မှုကို အလွန်လျော့နည်းစေပြီး သင့် AI စနစ်များကို ခိုင်မာယုံကြည်စိတ်ချရအောင် ထိန်းသိမ်းနိုင်ပါသည်။

# သင်ယူရမည့် ရည်မှန်းချက်များ

ဤသင်ခန်းစာအဆုံးတွင် သင်သည် -

- Model Context Protocol (MCP) မှ မိတ်ဆက်ပေးသော ထူးခြားသော လုံခြုံရေးအန္တရာယ်များကို ရှာဖွေရှင်းလင်းနိုင်မည်၊ အထူးသဖြင့် prompt injection, tool poisoning, အလွန်အကျွံခွင့်ပြုချက်များနှင့် ပစ္စည်းလမ်းကြောင်းအားနည်းချက်များကို ရှင်းပြနိုင်မည်။
- MCP လုံခြုံရေးအန္တရာယ်များအတွက် ထိရောက်သော ထိန်းချုပ်မှုများကို ဖော်ပြ၍ အသုံးချနိုင်မည်၊ ဥပမာအားဖြင့် ခိုင်မာသော အတည်ပြုခြင်း၊ အနည်းဆုံးခွင့်ပြုချက်၊ လုံခြုံသော token စီမံခန့်ခွဲမှုနှင့် ပစ္စည်းလမ်းကြောင်းအတည်ပြုခြင်း။
- Microsoft ၏ Prompt Shields, Azure Content Safety, နှင့် GitHub Advanced Security ကဲ့သို့သော ဖြေရှင်းချက်များကို နားလည်ပြီး MCP နှင့် AI အလုပ်များကို ကာကွယ်နိုင်မည်။
- Tool metadata ကို အတည်ပြုခြင်း၊ dynamic ပြောင်းလဲမှုများကို စောင့်ကြည့်ခြင်းနှင့် အကြောင်းမပြောသော prompt injection တိုက်ခိုက်မှုများကို ကာကွယ်ရန် အရေးကြီးမှုကို သိရှိနိုင်မည်။
- လုံခြုံရေးအကောင်းဆုံးလေ့လာမှုများကို MCP အကောင်အထည်ဖော်မှုတွင် ပေါင်းစပ်အသုံးချ၍ လုံခြုံရေးချိုးဖောက်မှု ဖြစ်ပေါ်နိုင်မှုနှင့် ထိခိုက်မှုကို လျော့နည်းစေနိုင်မည်။

# MCP လုံခြုံရေး ထိန်းချုပ်မှုများ

အရေးကြီးသော အရင်းအမြစ်များကို ဝင်ရောက်အသုံးပြုနိုင်သော စနစ်တိုင်းတွင် လုံခြုံရေး စိန်ခေါ်မှုများ ရှိသည်။ လုံခြုံရေး စိန်ခေါ်မှုများကို အခြေခံ လုံခြုံရေး ထိန်းချုပ်မှုများနှင့် အယူအဆများကို မှန်ကန်စွာ အသုံးချခြင်းဖြင့် ဖြေရှင်းနိုင်သည်။ MCP သည် အသစ်တစ်ခုအဖြစ် သတ်မှတ်ထားသဖြင့်၊ သတ်မှတ်ချက်များသည် အလွန်လျင်မြန်စွာ ပြောင်းလဲနေပြီး protocol တိုးတက်မှုအတိုင်း လုံခြုံရေး ထိန်းချုပ်မှုများလည်း တိုးတက်ကောင်းမွန်လာမည်ဖြစ်သည်။ ထိုကဲ့သို့ တိုးတက်လာခြင်းဖြင့် စီးပွားရေးအဖွဲ့အစည်းများနှင့် ရှိပြီးသား လုံခြုံရေး စနစ်များနှင့် ပိုမိုကောင်းမွန်စွာ ပေါင်းစည်းနိုင်မည်ဖြစ်သည်။

[Microsoft Digital Defense Report](https://aka.ms/mddr) တွင် ထုတ်ပြန်ထားသည့် သုတေသနအရ၊ ၉၈% အထိ လုံခြုံရေးချိုးဖောက်မှုများကို ခိုင်မာသော လုံခြုံရေး စနစ်နှင့် အကောင်းဆုံး ကာကွယ်မှုဖြင့် ကာကွယ်နိုင်ကြောင်း ဖော်ပြထားသည်။ လုံခြုံရေး အခြေခံစနစ်များ၊ လုံခြုံသော ကုဒ်ရေးခြင်းနည်းလမ်းများနှင့် ပစ္စည်းလမ်းကြောင်း လုံခြုံရေးကို မှန်ကန်စွာ လုပ်ဆောင်ခြင်းသည် လုံခြုံရေး အန္တရာယ် လျော့နည်းစေရန် အကျိုးသက်ရောက်မှု အများဆုံးဖြစ်ကြောင်း သိရှိရသည်။

MCP ကို အသုံးပြုစဉ် လုံခြုံရေး အန္တရာယ်များကို မည်သို့ စတင်ဖြေရှင်းနိုင်မည်ကို ကြည့်ကြရအောင်။

> **Note:** အောက်ပါ အချက်အလက်များမှာ **၂၀၂၅ ခုနှစ် မေ ၂၉ ရက်** အခြေအနေအရ မှန်ကန်ပါသည်။ MCP protocol သည် ဆက်လက်တိုးတက်နေပြီး အနာဂတ်တွင် အသစ်သော အတည်ပြုမှု ပုံစံများနှင့် ထိန်းချုပ်မှုများ ထည့်သွင်းနိုင်ပါသည်။ နောက်ဆုံးရ အချက်အလက်များနှင့် လမ်းညွှန်ချက်များအတွက် [MCP Specification](https://spec.modelcontextprotocol.io/) နှင့် တရားဝင် [MCP GitHub repository](https://github.com/modelcontextprotocol) နှင့် [security best practice page](https://modelcontextprotocol.io/specification/draft/basic/security_best_practices) ကို အမြဲ လေ့လာပါ။

### ပြဿနာအကြောင်းအရာ  
မူလ MCP သတ်မှတ်ချက်တွင် ဖန်တီးသူများသည် ကိုယ်ပိုင် အတည်ပြုမှု ဆာဗာရေးရန် မျှော်လင့်ထားသည်။ ၎င်းသည် OAuth နှင့် ဆက်စပ် လုံခြုံရေး ကန့်သတ်ချက်များကို သိရှိထားရန် လိုအပ်သည်။ MCP ဆာဗာများသည် OAuth 2.0 Authorization Servers အဖြစ် လုပ်ဆောင်ကာ အသုံးပြုသူ အတည်ပြုမှုကို တိုက်ရိုက် စီမံခန့်ခွဲသည်၊ Microsoft Entra ID ကဲ့သို့ ပြင်ပဝန်ဆောင်မှုသို့ မပေးအပ်ပါ။ **၂၀၂၅ ခုနှစ် ဧပြီ ၂၆ ရက်** မှစ၍ MCP သတ်မှတ်ချက်တွင် MCP ဆာဗာများသည် အသုံးပြုသူ အတည်ပြုမှုကို ပြင်ပဝန်ဆောင်မှုသို့ ပေးအပ်နိုင်ရန် ခွင့်ပြုထားသည်။

### အန္တရာယ်များ
- MCP ဆာဗာတွင် ခွင့်ပြုချက် အချက်အလက်များ မမှန်ကန်စွာ ဖွဲ့စည်းထားခြင်းကြောင့် ကိုယ်ရေးကိုယ်တာ ဒေတာ ထွက်ပေါက်ခြင်းနှင့် မမှန်ကန်သော ဝင်ရောက်ခွင့် ထိန်းချုပ်မှုများ ဖြစ်ပေါ်နိုင်သည်။
- ဒေသတွင်း MCP ဆာဗာတွင် OAuth token ခိုးယူခံရခြင်း။ ခိုးယူခံရပါက ထို token ကို အသုံးပြု၍ MCP ဆာဗာကို မတရား impersonate ပြုလုပ်ကာ OAuth token ရည်ရွယ်ထားသော ဝန်ဆောင်မှုမှ အရင်းအမြစ်များနှင့် ဒေတာများကို ဝင်ရောက်နိုင်သည်။

#### Token Passthrough
Token passthrough သည် authorization သတ်မှတ်ချက်တွင် တိတိကျကျ တားမြစ်ထားပြီး အောက်ပါ လုံခြုံရေး အန္တရာယ်များ ဖြစ်ပေါ်စေသည်။

#### လုံခြုံရေး ထိန်းချုပ်မှုများကို လွှဲပြောင်းခြင်း
MCP ဆာဗာ သို့မဟုတ် downstream API များသည် rate limiting, request validation, traffic monitoring ကဲ့သို့သော အရေးကြီးသော လုံခြုံရေး ထိန်းချုပ်မှုများကို token audience သို့မဟုတ် အခြား credential ကန့်သတ်ချက်များအပေါ် မူတည်၍ အကောင်အထည်ဖော်နိုင်သည်။ Clients များသည် MCP ဆာဗာမှ token မမှန်ကန်စွာ အတည်ပြုခြင်းမပြုဘဲ သို့မဟုတ် token များကို သတ်မှတ်ထားသော ဝန်ဆောင်မှုအတွက် မဖြစ်စေရန် စစ်ဆေးခြင်းမပြုဘဲ downstream API များနှင့် တိုက်ရိုက် အသုံးပြုနိုင်ပါက ထိုထိန်းချုပ်မှုများကို ကျော်လွှားသွားမည်ဖြစ်သည်။

#### တာဝန်ယူမှုနှင့် စစ်ဆေးမှု ပြဿနာများ
MCP ဆာဗာသည် upstream မှ ထုတ်ပေးသော access token ဖြင့် ခေါ်ဆိုသော MCP Clients များကို ခွဲခြားသိရှိ၍ မရနိုင်ပါ။  
Downstream Resource Server ၏ မှတ်တမ်းများတွင် token များကို တင်ပို့နေသော MCP ဆာဗာမဟုတ်ဘဲ အခြား အရင်းအမြစ်မှ လာသော တောင်းဆိုမှုများအဖြစ် ပြသနိုင်သည်။  
ဤအချက်များကြောင့် ဖြစ်ရပ်မှန် စုံစမ်းစစ်ဆေးခြင်း၊ ထိန်းချုပ်မှုများနှင့် စစ်ဆေးမှုများ ပြုလုပ်ရခက်ခဲစေသည်။  
MCP ဆာဗာသည် token များ၏ အခွင့်အရေးများ (ဥပမာ roles, privileges, audience) သို့မဟုတ် အခြား metadata များကို စစ်ဆေးခြင်းမပြုဘဲ token များကို ဖြတ်သန်းပေးပါက ခိုးယူထားသော token ကိုင်ဆောင်ထားသူ မကောင်းဆိုးဝါးသူသည် MCP ဆာဗာကို ဒေတာ ထွက်ပေါက်အတွက် proxy အဖြစ် အသုံးပြုနိုင်သည်။

#### ယုံကြည်မှု နယ်နိမိတ် ပြဿနာများ
Downstream Resource Server သည် သတ်မှတ်ထားသော အဖွဲ့အစည်းများကို ယုံကြည်မှု ပေးသည်။ ယုံကြည်မှုတွင် မူလအရင်းအမြစ် သို့မဟုတ် client အပြုအမူ ပုံစံများအပေါ် အယူအဆများ ပါဝင်နိုင်သည်။ ယုံကြည်မှု နယ်နိမိတ်ကို ချိုးဖောက်ခြင်းကြောင့် မမျှော်လင့်ထားသော ပြဿနာများ ဖြစ်ပေါ်နိုင်သည်။  
Token ကို ဝန်ဆောင်မှုများစွာမှ သက်ဆိုင်ရာ စစ်ဆေးမှုမပြုဘဲ လက်ခံပါက ဝန်ဆောင်မှုတစ်ခုကို ခိုးယူသူသည် အခြား ဝန်ဆောင်မှုများကိုလည်း token ဖြင့် ဝင်ရောက်နိုင်သည်။

#### အနာဂတ် ကိုက်ညီမှု အန္တရာယ်
ယနေ့ MCP ဆာဗာသည် “pure proxy” အဖြစ် စတင်ခဲ့ပါကလည်း နောက်ပိုင်းတွင် လုံခြုံရေး ထိန်းချုပ်မှုများ ထည့်သွင်းရန် လိုအပ်နိုင်သည်။ token audience ကို သေချာခွဲခြားထားခြင်းဖြင့် လုံခြုံရေး မော်ဒယ် တိုးတက်ရန် ပိုမိုလွယ်ကူစေသည်။

### လျော့နည်းစေရန် ထိန်းချုပ်မှုများ

**MCP ဆာဗာများသည် MCP ဆာဗာအတွက် တိတိကျကျ ထုတ်ပေးထားသော token မဟုတ်သော token များကို လက်ခံမရပါ။**

- **ခွင့်ပြုချက် အချက်အလက်များကို ပြန်လည်သုံးသပ်၍ ခိုင်မာစေပါ။** MCP ဆာဗာ၏ ခွင့်ပြုချက် အကောင်အထည်ဖော်မှုကို သေချာစွာ စစ်ဆေး၍ ရည်ရွယ်ထားသော အသုံးပြုသူများနှင့် client များသာ အရေးကြီးသော အရင်းအမြစ်များကို ဝင်ရောက်ခွင့်ရှိစေရန် သေချာစေပါ။ လက်တွေ့ လမ်းညွှန်ချက်များအတွက် [Azure API Management Your Auth Gateway For MCP Servers | Microsoft Community Hub](https://techcommunity.microsoft.com/blog/integrationsonazureblog/azure-api-management-your-auth-gateway-for-mcp-servers/4402690) နှင့် [Using Microsoft Entra ID To Authenticate With MCP Servers Via Sessions - Den Delimarsky](https://den.dev/blog/mcp-server-auth-entra-id-session/) ကို ကြည့်ရှုပါ။
- **လုံခြုံသော token အသုံးပြုမှုများကို အကောင်အထည်ဖော်ပါ။** [Microsoft ၏ token အတည်ပြုခြင်းနှင့် အသက်တာကာလအတွက် အကောင်းဆုံးလေ့လာမှုများ](https://learn.microsoft.com/en-us/entra/identity-platform/access-tokens) ကို လိုက်နာကာ access token မမှန်ကန်စွာ အသုံးပြုခြင်း၊ token ပြန်လည်အသုံးပြုခြင်း သို့မဟုတ် ခိုးယူခြင်း အန္တရာယ်များကို လျော့နည်းစေပါ။
- **Token သိမ်းဆည်းမှုကို ကာကွယ်ပါ။** token များကို အမြဲ လုံခြုံစွာ သိမ်းဆည်းပြီး သိုလှောင်ရာတွင် နှင့် လမ်းကြောင်းပေါ်တွင် စာရင်းအင်းကာကွယ်မှု (encryption) ကို အသုံးပြုပါ။ အကောင်အထည်ဖော်ရန် အကြံပြုချက်များအတွက် [Use secure token storage and encrypt tokens](https://youtu.be/uRdX37EcCwg?si=6fSChs1G4glwXRy2) ကို ကြည့်ရှုပါ။

# MCP ဆာဗာများအတွက် အလွန်အကျွံခွင့်ပြုချက်များ

### ပြဿနာအကြောင်းအရာ  
MCP ဆာဗာများသည် ဝင်ရောက်နေသော ဝန်ဆောင်မှု/အရင်းအမြစ်များအတွက် အလွန်အကျွံခွင့်ပြုချက်များ ရရှိထားနိုင်သည်။ ဥပမာအားဖြင့် AI အရောင်းဆိုင်ရာ အက်ပလီကေးရှင်းတစ်ခုတွင် ပါဝင်သော MCP ဆာဗာသည် စီးပွားရေး ဒေတာသိုလှောင်ရာမှ အရောင်းဆိုင်ရာ ဒေတာများကိုသာ ဝင်ရောက်ခွင့်ရှိသင့်ပြီး သိုလှောင်ရာရှိ ဖိုင်အားလုံးကို မဝင်ရောက်ခွင့်ရှိသင့်ပါ။ အနည်းဆုံးခွင့်ပြုချက် သဘောတရား (Principle of Least Privilege) အရ၊ တာဝန်ထမ်းဆောင်ရန် လိုအပ်သည့် ခွင့်ပြုချက်ထက် မပိုရသင့်ပါ။ AI သည် လွယ်ကူပြောင်းလဲနိုင်စေရန် အတွက် လိုအပ်သော ခွင့်ပြုချက်များကို တိတိကျကျ သတ်မှတ်ရန် အခက်အခဲရှိသည်။

### အန္တရာယ်များ  
- အလွန်အကျွံခွင့်ပြုချက်များ ပေးခြင်းကြောင့် MCP ဆာဗာ မရည်ရွယ်ထားသော ဒေတာများ ထွက်ပေါက်ခြင်း သို့မဟုတ် ပြင်ဆင်ခြင်း ဖြစ်ပေါ်နိုင်သည်။ ဒါ့အပြင် ဒေတာသည် ကိုယ်ရေးကိုယ်တာ သတင်းအချက်အလက် (PII) ဖြစ်ပါက ကိုယ်ရေးကိုယ်တာ လုံခြုံမှု ပြဿနာ ဖြစ်ပေါ်နိုင်သည်။

### လျော့နည်းစေရန် ထိန်းချုပ်မှုများ  
- **အနည်းဆုံးခွင့်ပြုချက် သဘောတရားကို အသုံးချပါ။** MCP ဆာဗာအား လိုအပ်သည့် တာဝန်များကိုသာ လုပ်ဆောင်နိုင်ရန် အနည်းဆုံး ခွင့်ပြုချက်များပေးပါ။ ဤခွင့်ပြုချက်များ
Supply chain လုံခြုံရေးသည် AI ခေတ်တွင် အခြေခံဖြစ်နေဆဲဖြစ်သော်လည်း သင့် supply chain အဖြစ် သတ်မှတ်ထားသည့် အရာများ၏ အကျယ်အဝန်းမှာ တိုးချဲ့လာပါပြီ။ ရိုးရာကုဒ်ပက်ကေ့ဂျ်များအပြင် foundation models, embeddings services, context providers, နှင့် third-party APIs အပါအဝင် AI နှင့်ဆက်စပ်သော အစိတ်အပိုင်းများအားလုံးကို တိကျစွာ စစ်ဆေးပြီး စောင့်ကြည့်ရမည်ဖြစ်သည်။ ၎င်းတို့အနက် တစ်ခုခုမှ မှားယွင်းစွာ စီမံခန့်ခွဲမထားပါက အန္တရာယ်များ သို့မဟုတ် ချို့ယွင်းချက်များ ဖြစ်ပေါ်နိုင်ပါသည်။

**AI နှင့် MCP အတွက် အဓိက supply chain လုံခြုံရေး လေ့ကျင့်မှုများ**
- **ပေါင်းစပ်မှုမပြုမီ အစိတ်အပိုင်းအားလုံးကို စစ်ဆေးပါ။** ၎င်းတွင် open-source libraries များသာမက AI မော်ဒယ်များ၊ ဒေတာရင်းမြစ်များနှင့် ပြင်ပ APIs များပါဝင်သည်။ မူရင်းအရင်းအမြစ်၊ လိုင်စင်နှင့် သိရှိထားသော ချို့ယွင်းချက်များကို အမြဲစစ်ဆေးပါ။
- **လုံခြုံသော deployment pipeline များကို ထိန်းသိမ်းပါ။** အလိုအလျောက် CI/CD pipeline များကို လုံခြုံရေး စစ်ဆေးမှုများနှင့် ပေါင်းစပ်၍ ပြဿနာများကို အစောဆုံး ဖော်ထုတ်နိုင်စေရန် အသုံးပြုပါ။ ယုံကြည်စိတ်ချရသော artifacts များသာ production သို့ တင်ပို့ပါစေ။
- **ဆက်လက်စောင့်ကြည့်ခြင်းနှင့် စစ်ဆေးခြင်းများ ပြုလုပ်ပါ။** မော်ဒယ်များနှင့် ဒေတာဝန်ဆောင်မှုများအပါအဝင် အားလုံးသော အားထားမှုများကို ဆက်လက်စောင့်ကြည့်ပြီး supply chain တိုက်ခိုက်မှုသစ်များ သို့မဟုတ် ချို့ယွင်းချက်များကို ရှာဖွေပါ။
- **အနည်းဆုံးခွင့်ပြုချက်နှင့် ဝင်ရောက်ခွင့် ထိန်းချုပ်မှုများကို အသုံးပြုပါ။** MCP ဆာဗာ၏ လုပ်ဆောင်မှုအတွက် လိုအပ်သည့် မော်ဒယ်များ၊ ဒေတာများနှင့် ဝန်ဆောင်မှုများကိုသာ ဝင်ရောက်ခွင့်ပေးပါ။
- **အန္တရာယ်များကို အမြန်တုံ့ပြန်ပါ။** ချို့ယွင်းသွားသော အစိတ်အပိုင်းများကို ပြင်ဆင်ခြင်း သို့မဟုတ် အစားထိုးခြင်း၊ လျှို့ဝှက်ချက်များ သို့မဟုတ် အသိအမှတ်ပြုချက်များကို ပြောင်းလဲခြင်းလုပ်ငန်းစဉ်များကို ရှိထားပါ။

[GitHub Advanced Security](https://github.com/security/advanced-security) သည် secret scanning, dependency scanning, နှင့် CodeQL analysis ကဲ့သို့သော လုပ်ဆောင်ချက်များကို ပံ့ပိုးပေးသည်။ ၎င်းကိရိယာများကို [Azure DevOps](https://azure.microsoft.com/en-us/products/devops) နှင့် [Azure Repos](https://azure.microsoft.com/en-us/products/devops/repos/) နှင့် ပေါင်းစပ်၍ ကုဒ်နှင့် AI supply chain အစိတ်အပိုင်းများအတွင်းရှိ ချို့ယွင်းချက်များကို အဖွဲ့များက ရှာဖွေကာ လျော့နည်းစေရန် ကူညီပေးသည်။

Microsoft သည် ထုတ်ကုန်အားလုံးအတွက် supply chain လုံခြုံရေး လေ့ကျင့်မှုများကို အတွင်းပိုင်းတွင် ကျယ်ပြန့်စွာ အသုံးပြုလျက်ရှိသည်။ [The Journey to Secure the Software Supply Chain at Microsoft](https://devblogs.microsoft.com/engineering-at-microsoft/the-journey-to-secure-the-software-supply-chain-at-microsoft/) တွင် ပိုမိုသိရှိနိုင်ပါသည်။


# MCP အကောင်အထည်ဖော်မှု၏ လုံခြုံရေး အခြေအနေကို မြှင့်တင်ပေးမည့် တည်ငြိမ်ပြီး သက်ဆိုင်သော လုံခြုံရေး လေ့ကျင့်မှုများ

MCP အကောင်အထည်ဖော်မှုသည် ၎င်းတည်ဆောက်ထားသော အဖွဲ့အစည်း၏ ပတ်ဝန်းကျင်ရှိ လုံခြုံရေး အခြေအနေကို ဆက်ခံရရှိသဖြင့် MCP ကို သင့် AI စနစ်များ၏ အစိတ်အပိုင်းတစ်ခုအဖြစ် လုံခြုံရေးအရ စဉ်းစားရာတွင် သင့်လက်ရှိ လုံခြုံရေး အခြေအနေကို မြှင့်တင်ရန် အကြံပြုသည်။ အောက်ပါ တည်ငြိမ်ပြီး သက်ဆိုင်သော လုံခြုံရေး ထိန်းချုပ်မှုများမှာ အထူးသင့်တော်ပါသည်-

- သင့် AI အက်ပလီကေးရှင်းတွင် လုံခြုံသော ကုဒ်ရေးသားမှု လေ့ကျင့်မှုများ - [OWASP Top 10](https://owasp.org/www-project-top-ten/) နှင့် [OWASP Top 10 for LLMs](https://genai.owasp.org/download/43299/?tmstv=1731900559) တို့ကို ကာကွယ်ရန်၊ လျှို့ဝှက်ချက်များနှင့် token များအတွက် လုံခြုံသော vault များ အသုံးပြုခြင်း၊ အက်ပလီကေးရှင်းအစိတ်အပိုင်းအားလုံးအကြား အဆုံးမှ အဆုံး လုံခြုံသော ဆက်သွယ်မှုများကို အကောင်အထည်ဖော်ခြင်း စသည်တို့။
- ဆာဗာကို ခိုင်မာစွာ ပြင်ဆင်ခြင်း - မဖြစ်မနေ MFA အသုံးပြုခြင်း၊ patch များကို အမြဲတမ်း နောက်ဆုံးထားခြင်း၊ ဝင်ရောက်ခွင့်အတွက် တတိယပါတီ အထောက်အပံ့ပေးသူနှင့် ဆက်သွယ်ခြင်း စသည်။
- စက်ပစ္စည်းများ၊ အခြေခံအဆောက်အအုံနှင့် အက်ပလီကေးရှင်းများကို patch များဖြင့် နောက်ဆုံးထားခြင်း။
- လုံခြုံရေး စောင့်ကြည့်မှု - AI အက်ပလီကေးရှင်း (MCP client/servers အပါအဝင်) ၏ မှတ်တမ်းတင်ခြင်းနှင့် စောင့်ကြည့်မှုကို အကောင်အထည်ဖော်ပြီး အထူး SIEM တစ်ခုသို့ ထိုမှတ်တမ်းများကို ပို့၍ မမှန်ကန်သော လှုပ်ရှားမှုများကို ရှာဖွေခြင်း။
- Zero trust architecture - AI အက်ပလီကေးရှင်း တစ်ခု ချို့ယွင်းခဲ့ပါက lateral movement ကို လျော့နည်းစေရန် အစိတ်အပိုင်းများကို ကွန်ယက်နှင့် အထောက်အထား ထိန်းချုပ်မှုများဖြင့် သက်ဆိုင်ရာ နည်းလမ်းဖြင့် ခွဲခြားထားခြင်း။

# အဓိက သင်ခန်းစာများ

- လုံခြုံရေး အခြေခံအချက်များမှာ အရေးကြီးနေဆဲဖြစ်သည်။ Secure coding, least privilege, supply chain verification, နှင့် ဆက်လက်စောင့်ကြည့်မှုများသည် MCP နှင့် AI အလုပ်များအတွက် မရှိမဖြစ်လိုအပ်သည်။
- MCP သည် prompt injection, tool poisoning, နှင့် အလွန်အမင်းခွင့်ပြုချက်များကဲ့သို့သော အန္တရာယ်အသစ်များကို မိတ်ဆက်ပေးပြီး ရိုးရာနှင့် AI အထူးထိန်းချုပ်မှုများနှစ်မျိုးလုံး လိုအပ်သည်။
- Microsoft Entra ID ကဲ့သို့သော ပြင်ပ အထောက်အထားပေးသူများကို အသုံးပြု၍ ခိုင်မာသော အတည်ပြုခြင်း၊ ခွင့်ပြုခြင်းနှင့် token စီမံခန့်ခွဲမှု လေ့ကျင့်မှုများကို အသုံးပြုပါ။
- Tool metadata ကို စစ်ဆေးခြင်း၊ dynamic ပြောင်းလဲမှုများကို စောင့်ကြည့်ခြင်းနှင့် Microsoft Prompt Shields ကဲ့သို့သော ဖြေရှင်းနည်းများကို အသုံးပြုခြင်းဖြင့် အတိုက်အခံ prompt injection နှင့် tool poisoning ကို ကာကွယ်ပါ။
- မော်ဒယ်များ၊ embeddings များနှင့် context providers များအပါအဝင် သင့် AI supply chain အတွင်းရှိ အစိတ်အပိုင်းအားလုံးကို ကုဒ်အားထားမှုများနှင့် တူညီသော တိကျမှုဖြင့် ကိုင်တွယ်ပါ။
- MCP သတ်မှတ်ချက်များ ပြောင်းလဲမှုများနှင့် အတူ နောက်ဆုံးပေါ်ဖြစ်နေစေရန် နှင့် လုံခြုံသော စံနှုန်းများ ဖန်တီးရာတွင် အသိုင်းအဝိုင်းကို ပါဝင်ဆောင်ရွက်ပါ။

# အပိုဆောင်း အရင်းအမြစ်များ

- [Microsoft Digital Defense Report](https://aka.ms/mddr)
- [MCP Specification](https://spec.modelcontextprotocol.io/)
- [Prompt Injection in MCP (Simon Willison)](https://simonwillison.net/2025/Apr/9/mcp-prompt-injection/)
- [Tool Poisoning Attacks (Invariant Labs)](https://invariantlabs.ai/blog/mcp-security-notification-tool-poisoning-attacks)
- [Rug Pulls in MCP (Wiz Security)](https://www.wiz.io/blog/mcp-security-research-briefing#remote-servers-22)
- [Prompt Shields Documentation (Microsoft)](https://learn.microsoft.com/azure/ai-services/content-safety/concepts/jailbreak-detection)
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [OWASP Top 10 for LLMs](https://genai.owasp.org/download/43299/?tmstv=1731900559)
- [GitHub Advanced Security](https://github.com/security/advanced-security)
- [Azure DevOps](https://azure.microsoft.com/products/devops)
- [Azure Repos](https://azure.microsoft.com/products/devops/repos/)
- [The Journey to Secure the Software Supply Chain at Microsoft](https://devblogs.microsoft.com/engineering-at-microsoft/the-journey-to-secure-the-software-supply-chain-at-microsoft/)
- [Secure Least-Privileged Access (Microsoft)](https://learn.microsoft.com/entra/identity-platform/secure-least-privileged-access)
- [Best Practices for Token Validation and Lifetime](https://learn.microsoft.com/entra/identity-platform/access-tokens)
- [Use Secure Token Storage and Encrypt Tokens (YouTube)](https://youtu.be/uRdX37EcCwg?si=6fSChs1G4glwXRy2)
- [Azure API Management as Auth Gateway for MCP](https://techcommunity.microsoft.com/blog/integrationsonazureblog/azure-api-management-your-auth-gateway-for-mcp-servers/4402690)
- [MCP Security Best Practice](https://modelcontextprotocol.io/specification/draft/basic/security_best_practices)
- [Using Microsoft Entra ID to Authenticate with MCP Servers](https://den.dev/blog/mcp-server-auth-entra-id-session/)

### Next 

Next: [Chapter 3: Getting Started](../03-GettingStarted/README.md)

**အကြောင်းကြားချက်**  
ဤစာတမ်းကို AI ဘာသာပြန်ဝန်ဆောင်မှု [Co-op Translator](https://github.com/Azure/co-op-translator) ဖြင့် ဘာသာပြန်ထားပါသည်။ ကျွန်ုပ်တို့သည် တိကျမှန်ကန်မှုအတွက် ကြိုးစားသော်လည်း အလိုအလျောက် ဘာသာပြန်ခြင်းတွင် အမှားများ သို့မဟုတ် မှားယွင်းချက်များ ပါဝင်နိုင်ကြောင်း သတိပြုပါရန် မေတ္တာရပ်ခံအပ်ပါသည်။ မူရင်းစာတမ်းကို မူလဘာသာဖြင့်သာ တရားဝင်အရင်းအမြစ်အဖြစ် ယူဆသင့်ပါသည်။ အရေးကြီးသော အချက်အလက်များအတွက် လူ့ဘာသာပြန်ပညာရှင်မှ ဘာသာပြန်ခြင်းကို အကြံပြုပါသည်။ ဤဘာသာပြန်ချက်ကို အသုံးပြုရာမှ ဖြစ်ပေါ်လာနိုင်သည့် နားလည်မှုမှားယွင်းမှုများအတွက် ကျွန်ုပ်တို့ တာဝန်မယူပါ။