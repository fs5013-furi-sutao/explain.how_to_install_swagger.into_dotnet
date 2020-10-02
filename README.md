# ASP.NET Core アプリに Swagger を導入する方法
## Swagger とは
Swagger とは、RESTful API の作成を補助するオープンソースのフレームワークのこと。 また、このフレームワークにおいて標準化されているドキュメント仕様そのものを指す言葉でもある。

## Swashbuckle
ASP.NET Core で Swagger を使うには、Swashbuckle パッケージを使う。

Swashbuckle には、次の 3 つの主要コンポーネントがある。

- **Swashbuckle.AspNetCore.Swagger**：  
SwaggerDocument オブジェクトを JSON エンドポイントとして公開するための Swagger オブジェクトモデルとミドルウェア。

- **Swashbuckle.AspNetCore.SwaggerGen**：  
SwaggerDocument ルート、コントローラー、およびモデルから直接オブジェクトを構築する Swagger ジェネレータ。通常、Swagger エンドポイントミドルウェアと組み合わせて、SwaggerJSON を自動的に公開する。

- **Swashbuckle.AspNetCore.SwaggerUI**：  
SwaggerUI ツールの埋め込みバージョン。Swagger JSON を解釈して、WebAPI 機能を記述するための豊富でカスタマイズ可能なエクスペリエンスを構築する。これには、パブリックメソッド用の組み込みテストハーネスが含まれている。

## パッケージのインストール
Swashbuckle は、次の方法で追加できる。

### VSCode の場合
Nuget Package Manager で Swashbuckle 5.5.0 を追加する。

### .NET Core CLI の場合
```console
dotnet add TodoApi.csproj package Swashbuckle.AspNetCore -v 5.5.0
```

## Swaggerミドルウェアを追加・構成する
Startup.ConfigureServices メソッドのサービスコレクションに Swagger ジェネレーターを追加する。

Startup.cs:
```
public void ConfigureServices(IServiceCollection services)
{
    // 1 つ以上の SwaggerDocument を定義して、Swagger ジェネレータを登録する
    services.AddSwaggerGen();
}
```

Startup.Configure メソッドで、生成された JSON ドキュメントと SwaggerUI を提供するためのミドルウェアを有効にする。
Startup.cs:
```
public void Configure(IApplicationBuilder app)
{
    // 生成された Swagger を JSON エンドポイントとして提供するミドルウェアに対して有効にする
    app.UseSwagger();

    // ミドルウェアが swagger-ui（HTML、JS、CSSなど）を提供することを有効にする。
    // Swagger JSONエンドポイントを指定する。
    app.UseSwaggerUI(c =>
    {
        c.SwaggerEndpoint("/swagger/v1/swagger.json", "My API V1");
    });

    app.UseRouting();
    app.UseEndpoints(endpoints =>
    {
        endpoints.MapControllers();
    });
}
```

この UseSwaggerUI メソッド呼び出しにより、静的ファイルミドルウェアが有効になす。

アプリを起動し、`http://localhost:<port>/swagger/v1/swagger.json` に移動する。
