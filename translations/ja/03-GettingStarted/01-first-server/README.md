<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "ba767f2f54d704d19bb886389228d285",
  "translation_date": "2025-07-04T16:15:49+00:00",
  "source_file": "03-GettingStarted/01-first-server/README.md",
  "language_code": "ja"
}
-->
# MCPのはじめ方

Model Context Protocol（MCP）の最初の一歩へようこそ！MCPが初めての方も、理解を深めたい方も、このガイドでは基本的なセットアップと開発の流れを丁寧に解説します。MCPがAIモデルとアプリケーションのシームレスな連携をどのように実現するかを理解し、MCP対応ソリューションの構築とテストのための環境準備を素早く行う方法を学びましょう。

> TLDR; AIアプリを作るなら、LLM（大規模言語モデル）にツールやリソースを追加して知識を増やせることはご存知でしょう。しかし、それらのツールやリソースをサーバーに置くと、LLMの有無にかかわらず、どのクライアントからでもアプリとサーバーの機能を利用できます。

## 概要

このレッスンでは、MCP環境のセットアップと最初のMCPアプリケーションの構築に関する実践的な手順を紹介します。必要なツールやフレームワークの準備、基本的なMCPサーバーの構築、ホストアプリケーションの作成、実装のテスト方法を学びます。

Model Context Protocol（MCP）は、アプリケーションがLLMにコンテキストを提供する方法を標準化したオープンプロトコルです。MCPはAIアプリケーションのUSB-Cポートのようなもので、AIモデルをさまざまなデータソースやツールに標準的に接続できる仕組みを提供します。

## 学習目標

このレッスンを終える頃には、以下ができるようになります：

- C#, Java, Python, TypeScript, JavaScriptでのMCP開発環境のセットアップ
- カスタム機能（リソース、プロンプト、ツール）を備えた基本的なMCPサーバーの構築とデプロイ
- MCPサーバーに接続するホストアプリケーションの作成
- MCP実装のテストとデバッグ

## MCP環境のセットアップ

MCPの開発を始める前に、開発環境を整え、基本的なワークフローを理解することが重要です。このセクションでは、スムーズにMCPを始めるための初期設定手順を案内します。

### 前提条件

MCP開発に入る前に、以下を準備してください：

- **開発環境**：選択した言語（C#, Java, Python, TypeScript, JavaScript）用
- **IDE/エディター**：Visual Studio、Visual Studio Code、IntelliJ、Eclipse、PyCharm、または任意のモダンなコードエディター
- **パッケージマネージャー**：NuGet、Maven/Gradle、pip、npm/yarn
- **APIキー**：ホストアプリケーションで使用予定のAIサービス用

## 基本的なMCPサーバー構成

MCPサーバーは通常、以下の要素で構成されます：

- **サーバー設定**：ポート、認証、その他の設定
- **リソース**：LLMに提供するデータやコンテキスト
- **ツール**：モデルが呼び出せる機能
- **プロンプト**：テキスト生成や構造化のためのテンプレート

以下はTypeScriptでの簡単な例です：

```typescript
import { Server, Tool, Resource } from "@modelcontextprotocol/typescript-server-sdk";

// Create a new MCP server
const server = new Server({
  port: 3000,
  name: "Example MCP Server",
  version: "1.0.0"
});

// Register a tool
server.registerTool({
  name: "calculator",
  description: "Performs basic calculations",
  parameters: {
    expression: {
      type: "string",
      description: "The math expression to evaluate"
    }
  },
  handler: async (params) => {
    const result = eval(params.expression);
    return { result };
  }
});

// Start the server
server.start();
```

上記コードでは：

- MCP TypeScript SDKから必要なクラスをインポートしています。
- 新しいMCPサーバーインスタンスを作成し設定しています。
- カスタムツール（`calculator`）をハンドラー関数とともに登録しています。
- MCPリクエストの受信を開始するためにサーバーを起動しています。

## テストとデバッグ

MCPサーバーのテストを始める前に、利用可能なツールとデバッグのベストプラクティスを理解することが重要です。効果的なテストはサーバーの期待通りの動作を保証し、問題の早期発見と解決に役立ちます。以下のセクションでは、MCP実装の検証に推奨される方法を紹介します。

MCPはサーバーのテストとデバッグを支援するツールを提供しています：

- **Inspectorツール**：グラフィカルなインターフェースでサーバーに接続し、ツール、プロンプト、リソースをテストできます。
- **curl**：コマンドラインツールcurlやHTTPコマンドを実行できる他のクライアントを使ってサーバーに接続可能です。

### MCP Inspectorの使い方

[MCP Inspector](https://github.com/modelcontextprotocol/inspector)は、以下のことを支援するビジュアルテストツールです：

1. **サーバー機能の発見**：利用可能なリソース、ツール、プロンプトを自動検出
2. **ツール実行のテスト**：さまざまなパラメーターを試し、リアルタイムで応答を確認
3. **サーバーメタデータの表示**：サーバー情報、スキーマ、設定を確認

```bash
# ex TypeScript, installing and running MCP Inspector
npx @modelcontextprotocol/inspector node build/index.js
```

上記コマンドを実行すると、MCP Inspectorがブラウザでローカルのウェブインターフェースを起動します。登録済みのMCPサーバーや利用可能なツール、リソース、プロンプトのダッシュボードが表示されます。インターフェースを使ってツールの実行を対話的にテストしたり、サーバーメタデータを調査したり、リアルタイムの応答を確認できるため、MCPサーバーの実装検証とデバッグが容易になります。

以下はその画面例です：

![](../../../../translated_images/connected.73d1e042c24075d386cacdd4ee7cd748c16364c277d814e646ff2f7b5eefde85.ja.png)

## よくあるセットアップの問題と解決策

| 問題 | 可能な解決策 |
|-------|-------------------|
| 接続拒否 | サーバーが起動しているか、ポートが正しいか確認 |
| ツール実行エラー | パラメーターの検証やエラーハンドリングを見直す |
| 認証失敗 | APIキーや権限を確認 |
| スキーマ検証エラー | パラメーターが定義されたスキーマに合っているか確認 |
| サーバーが起動しない | ポートの競合や依存関係の不足をチェック |
| CORSエラー | クロスオリジンリクエスト用の適切なCORSヘッダーを設定 |
| 認証問題 | トークンの有効性や権限を確認 |

## ローカル開発

ローカルでの開発とテストには、MCPサーバーを直接マシン上で実行できます：

1. **サーバープロセスを起動**：MCPサーバーアプリケーションを実行
2. **ネットワーク設定**：サーバーが期待するポートでアクセス可能か確認
3. **クライアント接続**：`http://localhost:3000`のようなローカル接続URLを使用

```bash
# Example: Running a TypeScript MCP server locally
npm run start
# Server running at http://localhost:3000
```

## 最初のMCPサーバーを作る

前回のレッスンで[コアコンセプト](/01-CoreConcepts/README.md)を学びました。ここからはその知識を実際に活用していきましょう。

### サーバーでできること

コードを書く前に、サーバーが何をできるかを改めて確認しましょう：

MCPサーバーは例えば：

- ローカルファイルやデータベースにアクセス
- リモートAPIに接続
- 計算処理を実行
- 他のツールやサービスと連携
- ユーザーインターフェースを提供して対話可能にする

これでサーバーに何ができるか分かったので、さっそくコーディングを始めましょう。

## 演習：サーバーの作成

サーバーを作成するには、以下の手順を踏みます：

- MCP SDKをインストールする
- プロジェクトを作成し、構成を整える
- サーバーコードを書く
- サーバーをテストする

### -1- SDKのインストール

使用するランタイムによって少し異なるので、以下から選んでください：

生成AIはテキスト、画像、コードまで生成できます。

<details>
  <summary>TypeScript</summary>

  ```sh
  npm install @modelcontextprotocol/sdk zod
  npm install -D @types/node typescript
  ```

</details>

<details>
<summary>Python</summary>

```sh
# For server development
pip install "mcp[cli]"
```

</details>

<details>
<summary>.NET</summary>

```sh
dotnet new console -n McpCalculatorServer
cd McpCalculatorServer
```

</details>

<details>
<summary>Java</summary>

Javaの場合はSpring Bootプロジェクトを作成します：

```bash
curl https://start.spring.io/starter.zip \
  -d dependencies=web \
  -d javaVersion=21 \
  -d type=maven-project \
  -d groupId=com.example \
  -d artifactId=calculator-server \
  -d name=McpServer \
  -d packageName=com.microsoft.mcp.sample.server \
  -o calculator-server.zip
```

zipファイルを展開します：

```bash
unzip calculator-server.zip -d calculator-server
cd calculator-server
# optional remove the unused test
rm -rf src/test/java
```

*pom.xml*ファイルに以下の完全な設定を追加します：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    
    <!-- Spring Boot parent for dependency management -->
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>3.5.0</version>
        <relativePath />
    </parent>

    <!-- Project coordinates -->
    <groupId>com.example</groupId>
    <artifactId>calculator-server</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <name>Calculator Server</name>
    <description>Basic calculator MCP service for beginners</description>

    <!-- Properties -->
    <properties>
        <java.version>21</java.version>
        <maven.compiler.source>21</maven.compiler.source>
        <maven.compiler.target>21</maven.compiler.target>
    </properties>

    <!-- Spring AI BOM for version management -->
    <dependencyManagement>
        <dependencies>
            <dependency>
                <groupId>org.springframework.ai</groupId>
                <artifactId>spring-ai-bom</artifactId>
                <version>1.0.0-SNAPSHOT</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
        </dependencies>
    </dependencyManagement>

    <!-- Dependencies -->
    <dependencies>
        <dependency>
            <groupId>org.springframework.ai</groupId>
            <artifactId>spring-ai-starter-mcp-server-webflux</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-actuator</artifactId>
        </dependency>
        <dependency>
         <groupId>org.springframework.boot</groupId>
         <artifactId>spring-boot-starter-test</artifactId>
         <scope>test</scope>
      </dependency>
    </dependencies>

    <!-- Build configuration -->
    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <configuration>
                    <release>21</release>
                </configuration>
            </plugin>
        </plugins>
    </build>

    <!-- Repositories for Spring AI snapshots -->
    <repositories>
        <repository>
            <id>spring-milestones</id>
            <name>Spring Milestones</name>
            <url>https://repo.spring.io/milestone</url>
            <snapshots>
                <enabled>false</enabled>
            </snapshots>
        </repository>
        <repository>
            <id>spring-snapshots</id>
            <name>Spring Snapshots</name>
            <url>https://repo.spring.io/snapshot</url>
            <releases>
                <enabled>false</enabled>
            </releases>
        </repository>
    </repositories>
</project>
```

</details>

### -2- プロジェクトの作成

SDKをインストールしたら、次にプロジェクトを作成しましょう：

<details>
  <summary>TypeScript</summary>

  ```sh
  mkdir src
  npm install -y
  ```

</details>

<details>
  <summary>Python</summary>

  ```sh
  python -m venv venv
  venv\Scripts\activate
  ```

</details>

<details>
<summary>Java</summary>

```bash
cd calculator-server
./mvnw clean install -DskipTests
```

</details>

### -3- プロジェクトファイルの作成

<details>
  <summary>TypeScript</summary>
  
  以下の内容で*package.json*を作成します：
  
  ```json
  {
     "type": "module",
     "bin": {
       "weather": "./build/index.js"
     },
     "scripts": {
       "build": "tsc && node build/index.js"
     },
     "files": [
       "build"
     ]
  }
  ```

  以下の内容で*tsconfig.json*を作成します：

  ```json
  {
    "compilerOptions": {
      "target": "ES2022",
      "module": "Node16",
      "moduleResolution": "Node16",
      "outDir": "./build",
      "rootDir": "./src",
      "strict": true,
      "esModuleInterop": true,
      "skipLibCheck": true,
      "forceConsistentCasingInFileNames": true
    },
    "include": ["src/**/*"],
    "exclude": ["node_modules"]
  }
  ```

</details>

<details>
<summary>Python</summary>

*server.py*ファイルを作成します
</details>

<details>
<summary>.NET</summary>

必要なNuGetパッケージをインストールします：

```sh
dotnet add package ModelContextProtocol --prerelease
dotnet add package Microsoft.Extensions.Hosting
```

</details>

<details>
<summary>Java</summary>

Java Spring Bootプロジェクトでは、プロジェクト構成は自動で作成されます。

</details>

### -4- サーバーコードの作成

<details>
  <summary>TypeScript</summary>
  
  *index.ts*ファイルを作成し、以下のコードを追加します：

  ```typescript
  import { McpServer, ResourceTemplate } from "@modelcontextprotocol/sdk/server/mcp.js";
  import { StdioServerTransport } from "@modelcontextprotocol/sdk/server/stdio.js";
  import { z } from "zod";
   
  // Create an MCP server
  const server = new McpServer({
    name: "Demo",
    version: "1.0.0"
  });
  ```

  これでサーバーはできましたが、まだあまり機能しません。改善しましょう。
</details>

<details>
<summary>Python</summary>

```python
# server.py
from mcp.server.fastmcp import FastMCP

# Create an MCP server
mcp = FastMCP("Demo")
```

</details>

<details>
<summary>.NET</summary>

```csharp
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Hosting;
using Microsoft.Extensions.Logging;
using ModelContextProtocol.Server;
using System.ComponentModel;

var builder = Host.CreateApplicationBuilder(args);
builder.Logging.AddConsole(consoleLogOptions =>
{
    // Configure all logs to go to stderr
    consoleLogOptions.LogToStandardErrorThreshold = LogLevel.Trace;
});

builder.Services
    .AddMcpServer()
    .WithStdioServerTransport()
    .WithToolsFromAssembly();
await builder.Build().RunAsync();

// add features
```

</details>

<details>
<summary>Java</summary>

Javaでは、コアサーバーコンポーネントを作成します。まずメインアプリケーションクラスを修正します：

*src/main/java/com/microsoft/mcp/sample/server/McpServerApplication.java*:

```java
package com.microsoft.mcp.sample.server;

import org.springframework.ai.tool.ToolCallbackProvider;
import org.springframework.ai.tool.method.MethodToolCallbackProvider;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.context.annotation.Bean;
import com.microsoft.mcp.sample.server.service.CalculatorService;

@SpringBootApplication
public class McpServerApplication {

    public static void main(String[] args) {
        SpringApplication.run(McpServerApplication.class, args);
    }
    
    @Bean
    public ToolCallbackProvider calculatorTools(CalculatorService calculator) {
        return MethodToolCallbackProvider.builder().toolObjects(calculator).build();
    }
}
```

計算サービスを作成します *src/main/java/com/microsoft/mcp/sample/server/service/CalculatorService.java*:

```java
package com.microsoft.mcp.sample.server.service;

import org.springframework.ai.tool.annotation.Tool;
import org.springframework.stereotype.Service;

/**
 * Service for basic calculator operations.
 * This service provides simple calculator functionality through MCP.
 */
@Service
public class CalculatorService {

    /**
     * Add two numbers
     * @param a The first number
     * @param b The second number
     * @return The sum of the two numbers
     */
    @Tool(description = "Add two numbers together")
    public String add(double a, double b) {
        double result = a + b;
        return formatResult(a, "+", b, result);
    }

    /**
     * Subtract one number from another
     * @param a The number to subtract from
     * @param b The number to subtract
     * @return The result of the subtraction
     */
    @Tool(description = "Subtract the second number from the first number")
    public String subtract(double a, double b) {
        double result = a - b;
        return formatResult(a, "-", b, result);
    }

    /**
     * Multiply two numbers
     * @param a The first number
     * @param b The second number
     * @return The product of the two numbers
     */
    @Tool(description = "Multiply two numbers together")
    public String multiply(double a, double b) {
        double result = a * b;
        return formatResult(a, "*", b, result);
    }

    /**
     * Divide one number by another
     * @param a The numerator
     * @param b The denominator
     * @return The result of the division
     */
    @Tool(description = "Divide the first number by the second number")
    public String divide(double a, double b) {
        if (b == 0) {
            return "Error: Cannot divide by zero";
        }
        double result = a / b;
        return formatResult(a, "/", b, result);
    }

    /**
     * Calculate the power of a number
     * @param base The base number
     * @param exponent The exponent
     * @return The result of raising the base to the exponent
     */
    @Tool(description = "Calculate the power of a number (base raised to an exponent)")
    public String power(double base, double exponent) {
        double result = Math.pow(base, exponent);
        return formatResult(base, "^", exponent, result);
    }

    /**
     * Calculate the square root of a number
     * @param number The number to find the square root of
     * @return The square root of the number
     */
    @Tool(description = "Calculate the square root of a number")
    public String squareRoot(double number) {
        if (number < 0) {
            return "Error: Cannot calculate square root of a negative number";
        }
        double result = Math.sqrt(number);
        return String.format("√%.2f = %.2f", number, result);
    }

    /**
     * Calculate the modulus (remainder) of division
     * @param a The dividend
     * @param b The divisor
     * @return The remainder of the division
     */
    @Tool(description = "Calculate the remainder when one number is divided by another")
    public String modulus(double a, double b) {
        if (b == 0) {
            return "Error: Cannot divide by zero";
        }
        double result = a % b;
        return formatResult(a, "%", b, result);
    }

    /**
     * Calculate the absolute value of a number
     * @param number The number to find the absolute value of
     * @return The absolute value of the number
     */
    @Tool(description = "Calculate the absolute value of a number")
    public String absolute(double number) {
        double result = Math.abs(number);
        return String.format("|%.2f| = %.2f", number, result);
    }

    /**
     * Get help about available calculator operations
     * @return Information about available operations
     */
    @Tool(description = "Get help about available calculator operations")
    public String help() {
        return "Basic Calculator MCP Service\n\n" +
               "Available operations:\n" +
               "1. add(a, b) - Adds two numbers\n" +
               "2. subtract(a, b) - Subtracts the second number from the first\n" +
               "3. multiply(a, b) - Multiplies two numbers\n" +
               "4. divide(a, b) - Divides the first number by the second\n" +
               "5. power(base, exponent) - Raises a number to a power\n" +
               "6. squareRoot(number) - Calculates the square root\n" + 
               "7. modulus(a, b) - Calculates the remainder of division\n" +
               "8. absolute(number) - Calculates the absolute value\n\n" +
               "Example usage: add(5, 3) will return 5 + 3 = 8";
    }

    /**
     * Format the result of a calculation
     */
    private String formatResult(double a, String operator, double b, double result) {
        return String.format("%.2f %s %.2f = %.2f", a, operator, b, result);
    }
}
```

**本番環境向けのオプションコンポーネント：**

起動設定を作成します *src/main/java/com/microsoft/mcp/sample/server/config/StartupConfig.java*:

```java
package com.microsoft.mcp.sample.server.config;

import org.springframework.boot.CommandLineRunner;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class StartupConfig {
    
    @Bean
    public CommandLineRunner startupInfo() {
        return args -> {
            System.out.println("\n" + "=".repeat(60));
            System.out.println("Calculator MCP Server is starting...");
            System.out.println("SSE endpoint: http://localhost:8080/sse");
            System.out.println("Health check: http://localhost:8080/actuator/health");
            System.out.println("=".repeat(60) + "\n");
        };
    }
}
```

ヘルスコントローラーを作成します *src/main/java/com/microsoft/mcp/sample/server/controller/HealthController.java*:

```java
package com.microsoft.mcp.sample.server.controller;

import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;
import java.time.LocalDateTime;
import java.util.HashMap;
import java.util.Map;

@RestController
public class HealthController {
    
    @GetMapping("/health")
    public ResponseEntity<Map<String, Object>> healthCheck() {
        Map<String, Object> response = new HashMap<>();
        response.put("status", "UP");
        response.put("timestamp", LocalDateTime.now().toString());
        response.put("service", "Calculator MCP Server");
        return ResponseEntity.ok(response);
    }
}
```

例外ハンドラーを作成します *src/main/java/com/microsoft/mcp/sample/server/exception/GlobalExceptionHandler.java*:

```java
package com.microsoft.mcp.sample.server.exception;

import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.ExceptionHandler;
import org.springframework.web.bind.annotation.RestControllerAdvice;

@RestControllerAdvice
public class GlobalExceptionHandler {

    @ExceptionHandler(IllegalArgumentException.class)
    public ResponseEntity<ErrorResponse> handleIllegalArgumentException(IllegalArgumentException ex) {
        ErrorResponse error = new ErrorResponse(
            "Invalid_Input", 
            "Invalid input parameter: " + ex.getMessage());
        return new ResponseEntity<>(error, HttpStatus.BAD_REQUEST);
    }

    public static class ErrorResponse {
        private String code;
        private String message;

        public ErrorResponse(String code, String message) {
            this.code = code;
            this.message = message;
        }

        // Getters
        public String getCode() { return code; }
        public String getMessage() { return message; }
    }
}
```

カスタムバナーを作成します *src/main/resources/banner.txt*:

```text
_____      _            _       _             
 / ____|    | |          | |     | |            
| |     __ _| | ___ _   _| | __ _| |_ ___  _ __ 
| |    / _` | |/ __| | | | |/ _` | __/ _ \| '__|
| |___| (_| | | (__| |_| | | (_| | || (_) | |   
 \_____\__,_|_|\___|\__,_|_|\__,_|\__\___/|_|   
                                                
Calculator MCP Server v1.0
Spring Boot MCP Application
```

</details>

### -5- ツールとリソースの追加

以下のコードを追加してツールとリソースを作成します：

<details>
  <summary>TypeScript</summary>

  ```typescript
    server.tool("add",
    { a: z.number(), b: z.number() },
    async ({ a, b }) => ({
      content: [{ type: "text", text: String(a + b) }]
    })
  );

  server.resource(
    "greeting",
    new ResourceTemplate("greeting://{name}", { list: undefined }),
    async (uri, { name }) => ({
      contents: [{
        uri: uri.href,
        text: `Hello, ${name}!`
      }]
    })
  );
  ```

  ツールはパラメーター`a`と`b`を受け取り、以下の形式でレスポンスを返します：

  ```typescript
  {
    contents: [{
      type: "text", content: "some content"
    }]
  }
  ```

  リソースは文字列"greeting"でアクセスされ、パラメーター`name`を受け取り、ツールと似た形式のレスポンスを生成します：

  ```typescript
  {
    uri: "<href>",
    text: "a text"
  }
  ```

</details>

<details>
<summary>Python</summary>

```python
# Add an addition tool
@mcp.tool()
def add(a: int, b: int) -> int:
    """Add two numbers"""
    return a + b


# Add a dynamic greeting resource
@mcp.resource("greeting://{name}")
def get_greeting(name: str) -> str:
    """Get a personalized greeting"""
    return f"Hello, {name}!"
```

上記コードでは：

- パラメーター`a`と`p`（どちらも整数）を受け取る`add`ツールを定義しました。
- パラメーター`name`を受け取る`greeting`リソースを作成しました。

</details>

<details>
<summary>.NET</summary>

Program.csファイルに以下を追加します：

```csharp
[McpServerToolType]
public static class CalculatorTool
{
    [McpServerTool, Description("Adds two numbers")]
    public static string Add(int a, int b) => $"Sum {a + b}";
}
```

</details>

<details>
<summary>Java</summary>

ツールは前のステップで既に作成済みです。

</details>

### -6- 最終コード

サーバーを起動できるように最後のコードを追加しましょう：

<details>
<summary>TypeScript</summary>

```typescript
// Start receiving messages on stdin and sending messages on stdout
const transport = new StdioServerTransport();
await server.connect(transport);
```

全コードはこちらです：

```typescript
// index.ts
import { McpServer, ResourceTemplate } from "@modelcontextprotocol/sdk/server/mcp.js";
import { StdioServerTransport } from "@modelcontextprotocol/sdk/server/stdio.js";
import { z } from "zod";

// Create an MCP server
const server = new McpServer({
  name: "Demo",
  version: "1.0.0"
});

// Add an addition tool
server.tool("add",
  { a: z.number(), b: z.number() },
  async ({ a, b }) => ({
    content: [{ type: "text", text: String(a + b) }]
  })
);

// Add a dynamic greeting resource
server.resource(
  "greeting",
  new ResourceTemplate("greeting://{name}", { list: undefined }),
  async (uri, { name }) => ({
    contents: [{
      uri: uri.href,
      text: `Hello, ${name}!`
    }]
  })
);

// Start receiving messages on stdin and sending messages on stdout
const transport = new StdioServerTransport();
await server.connect(transport);
```

</details>

<details>
<summary>Python</summary>

```python
# server.py
from mcp.server.fastmcp import FastMCP

# Create an MCP server
mcp = FastMCP("Demo")


# Add an addition tool
@mcp.tool()
def add(a: int, b: int) -> int:
    """Add two numbers"""
    return a + b


# Add a dynamic greeting resource
@mcp.resource("greeting://{name}")
def get_greeting(name: str) -> str:
    """Get a personalized greeting"""
    return f"Hello, {name}!"
```

</details>

<details>
<summary>.NET</summary>

以下の内容でProgram.csファイルを作成します：

```csharp
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Hosting;
using Microsoft.Extensions.Logging;
using ModelContextProtocol.Server;
using System.ComponentModel;

var builder = Host.CreateApplicationBuilder(args);
builder.Logging.AddConsole(consoleLogOptions =>
{
    // Configure all logs to go to stderr
    consoleLogOptions.LogToStandardErrorThreshold = LogLevel.Trace;
});

builder.Services
    .AddMcpServer()
    .WithStdioServerTransport()
    .WithToolsFromAssembly();
await builder.Build().RunAsync();

[McpServerToolType]
public static class CalculatorTool
{
    [McpServerTool, Description("Adds two numbers")]
    public static string Add(int a, int b) => $"Sum {a + b}";
}
```

</details>

<details>
<summary>Java</summary>

メインアプリケーションクラスの完成形は以下の通りです：

```java
// McpServerApplication.java
package com.microsoft.mcp.sample.server;

import org.springframework.ai.tool.ToolCallbackProvider;
import org.springframework.ai.tool.method.MethodToolCallbackProvider;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.context.annotation.Bean;
import com.microsoft.mcp.sample.server.service.CalculatorService;

@SpringBootApplication
public class McpServerApplication {

    public static void main(String[] args) {
        SpringApplication.run(McpServerApplication.class, args);
    }
    
    @Bean
    public ToolCallbackProvider calculatorTools(CalculatorService calculator) {
        return MethodToolCallbackProvider.builder().toolObjects(calculator).build();
    }
}
```

</details>

### -7- サーバーのテスト

以下のコマンドでサーバーを起動します：

<details>
<summary>TypeScript</summary>

```sh
npm run build
```

</details>

<details>
<summary>Python</summary>

```sh
mcp run server.py
```

</details>

<details>
<summary>.NET</summary>

プロジェクトディレクトリにいることを確認してください：

```sh
cd McpCalculatorServer
dotnet run
```

</details>

<details>
<summary>Java</summary>

```bash
./mvnw clean install -DskipTests
java -jar target/calculator-server-0.0.1-SNAPSHOT.jar
```

</details>

### -8- Inspectorを使って実行

Inspectorはサーバーを起動し、対話的に操作して動作確認ができる便利なツールです。起動してみましょう：

> [!NOTE]
> "command"フィールドの表示は、使用しているランタイムに応じて異なる場合があります。

<details>
<summary>TypeScript</summary>

```sh
npx @modelcontextprotocol/inspector node build/index.js
```

または*package.json*に以下を追加して、`npm run inspect`で実行できます：  
`"inspector": "npx @modelcontextprotocol/inspector node build/index.js"`

次のユーザーインターフェースが表示されるはずです：

![Connect](../../../../translated_images/connect.141db0b2bd05f096fb1dd91273771fd8b2469d6507656c3b0c9df4b3c5473929.ja.png)

1. Connectボタンを選択してサーバーに接続します  
  サーバーに接続すると、次の画面が表示されます：

  ![Connected](../../../../translated_images/connected.73d1e042c24075d386cacdd4ee7cd748c16364c277d814e646ff2f7b5eefde85.ja.png)

1. 「Tools」から「listTools」を選択すると、「Add」が表示されます。「Add」を選択してパラメーターの値を入力してください。

  次のような応答が表示されます。これは「add」ツールの結果です：

  ![Result of running add](../../../../translated_images/ran-tool.a5a6ee878c1369ec1e379b81053395252a441799dbf23416c36ddf288faf8249.ja.png)

おめでとうございます、最初のサーバーを作成して実行することができました！

### 公式SDK

MCPは複数の言語向けに公式SDKを提供しています：

- [C# SDK](https://github.com/modelcontextprotocol/csharp-sdk) - Microsoftと共同でメンテナンス
- [Java SDK](https://github.com/modelcontextprotocol/java-sdk) - Spring AIと共同でメンテナンス
- [TypeScript SDK](https://github.com/modelcontextprotocol/typescript-sdk) - 公式のTypeScript実装
- [Python SDK](https://github.com/modelcontextprotocol/python-sdk) - 公式のPython実装
- [Kotlin SDK](https://github.com/modelcontextprotocol/kotlin-sdk) - 公式のKotlin実装
- [Swift SDK](https://github.com/modelcontextprotocol/swift-sdk) - Loopwork AIと共同でメンテナンス
- [Rust SDK](https://github.com/modelcontextprotocol/rust-sdk) - 公式のRust実装

## 重要なポイント

- MCPの開発環境は言語別SDKを使うことで簡単にセットアップできる
- MCPサーバーの構築は、明確なスキーマを持つツールの作成と登録が必要
- テストとデバッグは信頼性の高いMCP実装に不可欠

## サンプル

- [Java Calculator](../samples/java/calculator/README.md)
- [.Net Calculator](../../../../03-GettingStarted/samples/csharp)
- [JavaScript Calculator](../samples/javascript/README.md)
- [TypeScript Calculator](../samples/typescript/README.md)
- [Python Calculator](../../../../03-GettingStarted/samples/python)

## 課題

お好きなツールを使ってシンプルなMCPサーバーを作成してください：

1. 好きな言語（.NET、Java、Python、JavaScript）でツールを実装する
2. 入力パラメーターと戻り値を定義する
3. インスペクターツールを実行してサーバーが正しく動作することを確認する
4. さまざまな入力で実装をテストする

## 解答例

[Solution](./solution/README.md)

## 追加リソース

- [AzureでModel Context Protocolを使ったエージェントの構築](https://learn.microsoft.com/azure/developer/ai/intro-agents-mcp)
- [Azure Container AppsでのリモートMCP（Node.js/TypeScript/JavaScript）](https://learn.microsoft.com/samples/azure-samples/mcp-container-ts/mcp-container-ts/)
- [.NET OpenAI MCPエージェント](https://learn.microsoft.com/samples/azure-samples/openai-mcp-agent-dotnet/openai-mcp-agent-dotnet/)

## 次にやること

次へ：[MCPクライアントの使い方](../02-client/README.md)

**免責事項**：  
本書類はAI翻訳サービス「[Co-op Translator](https://github.com/Azure/co-op-translator)」を使用して翻訳されました。正確性を期しておりますが、自動翻訳には誤りや不正確な部分が含まれる可能性があります。原文の言語によるオリジナル文書が正式な情報源とみなされるべきです。重要な情報については、専門の人間による翻訳を推奨します。本翻訳の利用により生じたいかなる誤解や誤訳についても、当方は責任を負いかねます。