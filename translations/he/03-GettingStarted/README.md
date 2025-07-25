<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "97f1c99b5b12cf03d4b1be68b3636a4a",
  "translation_date": "2025-07-04T17:59:23+00:00",
  "source_file": "03-GettingStarted/README.md",
  "language_code": "he"
}
-->
## התחלה  

החלק הזה מורכב ממספר שיעורים:

- **1 השרת הראשון שלך**, בשיעור הראשון תלמד כיצד ליצור את השרת הראשון שלך ולבדוק אותו עם כלי המפקח, דרך חשובה לבדוק ולתקן את השרת שלך, [לשיעור](/03-GettingStarted/01-first-server/README.md)

- **2 לקוח**, בשיעור זה תלמד כיצד לכתוב לקוח שיכול להתחבר לשרת שלך, [לשיעור](/03-GettingStarted/02-client/README.md)

- **3 לקוח עם LLM**, דרך טובה יותר לכתוב לקוח היא להוסיף לו LLM כדי שיוכל "לנהל משא ומתן" עם השרת שלך על מה לעשות, [לשיעור](/03-GettingStarted/03-llm-client/README.md)

- **4 צריכת מצב סוכן GitHub Copilot ב-Visual Studio Code**. כאן נבחן כיצד להריץ את MCP Server שלנו מתוך Visual Studio Code, [לשיעור](/03-GettingStarted/04-vscode/README.md)

- **5 צריכה מ-SSE (Server Sent Events)** SSE הוא תקן לזרימה מהשרת ללקוח, המאפשר לשרתים לדחוף עדכונים בזמן אמת ללקוחות דרך HTTP [לשיעור](/03-GettingStarted/05-sse-server/README.md)

- **6 זרימת HTTP עם MCP (Streamable HTTP)**. תלמד על זרימת HTTP מודרנית, התראות התקדמות, וכיצד לממש שרתי ולקוחות MCP בזמן אמת וסקלאביליים באמצעות Streamable HTTP. [לשיעור](/03-GettingStarted/06-http-streaming/README.md)

- **7 שימוש ב-AI Toolkit עבור VSCode** לצריכה ובדיקת לקוחות ושרתים של MCP [לשיעור](/03-GettingStarted/07-aitk/README.md)

- **8 בדיקות**. כאן נתמקד במיוחד כיצד ניתן לבדוק את השרת והלקוח שלנו בדרכים שונות, [לשיעור](/03-GettingStarted/08-testing/README.md)

- **9 פריסה**. פרק זה יבחן דרכים שונות לפריסת פתרונות MCP שלך, [לשיעור](/03-GettingStarted/09-deployment/README.md)


פרוטוקול Model Context (MCP) הוא פרוטוקול פתוח שמאחד את הדרך שבה אפליקציות מספקות הקשר ל-LLMs. אפשר לחשוב על MCP כמו על חיבור USB-C לאפליקציות AI - הוא מספק דרך סטנדרטית לחבר מודלים של AI למקורות נתונים וכלים שונים.

## מטרות הלמידה

בסיום השיעור תוכל:

- להגדיר סביבות פיתוח ל-MCP ב-C#, Java, Python, TypeScript ו-JavaScript
- לבנות ולפרוס שרתי MCP בסיסיים עם תכונות מותאמות (משאבים, פרומפטים וכלים)
- ליצור אפליקציות מארחות שמתחברות לשרתי MCP
- לבדוק ולתקן יישומי MCP
- להבין את האתגרים הנפוצים בהגדרה ואת הפתרונות להם
- לחבר את יישומי MCP שלך לשירותי LLM פופולריים

## הגדרת סביבת MCP שלך

לפני שתתחיל לעבוד עם MCP, חשוב להכין את סביבת הפיתוח ולהבין את זרימת העבודה הבסיסית. חלק זה ינחה אותך בשלבי ההגדרה הראשוניים כדי להבטיח התחלה חלקה עם MCP.

### דרישות מוקדמות

לפני שתצלול לפיתוח MCP, ודא שיש לך:

- **סביבת פיתוח**: עבור השפה שבחרת (C#, Java, Python, TypeScript או JavaScript)
- **IDE/עורך**: Visual Studio, Visual Studio Code, IntelliJ, Eclipse, PyCharm או כל עורך קוד מודרני
- **מנהל חבילות**: NuGet, Maven/Gradle, pip או npm/yarn
- **מפתחות API**: עבור כל שירותי AI שתכננת להשתמש בהם באפליקציות המארחות שלך


### SDKs רשמיים

בפרקים הבאים תראה פתרונות שנבנו באמצעות Python, TypeScript, Java ו-.NET. להלן כל ה-SDKs הנתמכים רשמית.

MCP מספק SDKs רשמיים למספר שפות:
- [C# SDK](https://github.com/modelcontextprotocol/csharp-sdk) - מתוחזק בשיתוף עם Microsoft
- [Java SDK](https://github.com/modelcontextprotocol/java-sdk) - מתוחזק בשיתוף עם Spring AI
- [TypeScript SDK](https://github.com/modelcontextprotocol/typescript-sdk) - המימוש הרשמי של TypeScript
- [Python SDK](https://github.com/modelcontextprotocol/python-sdk) - המימוש הרשמי של Python
- [Kotlin SDK](https://github.com/modelcontextprotocol/kotlin-sdk) - המימוש הרשמי של Kotlin
- [Swift SDK](https://github.com/modelcontextprotocol/swift-sdk) - מתוחזק בשיתוף עם Loopwork AI
- [Rust SDK](https://github.com/modelcontextprotocol/rust-sdk) - המימוש הרשמי של Rust

## נקודות מפתח

- הגדרת סביבת פיתוח MCP היא פשוטה עם SDKs ספציפיים לשפה
- בניית שרתי MCP כוללת יצירה ורישום כלים עם סכימות ברורות
- לקוחות MCP מתחברים לשרתי ומודלים כדי לנצל יכולות מורחבות
- בדיקות ותיקונים חיוניים ליישומי MCP אמינים
- אפשרויות הפריסה נעות מפיתוח מקומי ועד פתרונות מבוססי ענן

## תרגול

יש לנו סט דוגמאות שמלווה את התרגילים שתראה בכל הפרקים בחלק זה. בנוסף, לכל פרק יש גם תרגילים ומשימות משלו

- [מחשבון Java](./samples/java/calculator/README.md)
- [מחשבון .Net](../../../03-GettingStarted/samples/csharp)
- [מחשבון JavaScript](./samples/javascript/README.md)
- [מחשבון TypeScript](./samples/typescript/README.md)
- [מחשבון Python](../../../03-GettingStarted/samples/python)

## משאבים נוספים

- [בניית סוכנים באמצעות Model Context Protocol ב-Azure](https://learn.microsoft.com/azure/developer/ai/intro-agents-mcp)
- [MCP מרוחק עם Azure Container Apps (Node.js/TypeScript/JavaScript)](https://learn.microsoft.com/samples/azure-samples/mcp-container-ts/mcp-container-ts/)
- [סוכן .NET OpenAI MCP](https://learn.microsoft.com/samples/azure-samples/openai-mcp-agent-dotnet/openai-mcp-agent-dotnet/)

## מה הלאה

הבא: [יצירת שרת MCP ראשון שלך](./01-first-server/README.md)

**כתב ויתור**:  
מסמך זה תורגם באמצעות שירות תרגום מבוסס בינה מלאכותית [Co-op Translator](https://github.com/Azure/co-op-translator). למרות שאנו שואפים לדיוק, יש לקחת בחשבון כי תרגומים אוטומטיים עלולים להכיל שגיאות או אי-דיוקים. המסמך המקורי בשפת המקור שלו נחשב למקור הסמכותי. למידע קריטי מומלץ להשתמש בתרגום מקצועי על ידי מתרגם אנושי. אנו לא נושאים באחריות לכל אי-הבנה או פרשנות שגויה הנובעת משימוש בתרגום זה.