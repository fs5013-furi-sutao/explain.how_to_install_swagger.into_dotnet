# ASP.NET Core アプリに Swagger を導入する方法
## Swagger とは
Swagger とは、RESTful API の作成を補助するオープンソースのフレームワークのこと。 また、このフレームワークにおいて標準化されているドキュメント仕様そのものを指す言葉でもある。

## Swashbuckle
ASP.NET Core で Swagger を使うには、Swashbuckle パッケージを使う。

Swashbuckle には、次の 3 つの主要コンポーネントがある。

- Swashbuckle.AspNetCore.Swagger：
SwaggerDocumentオブジェクトをJSONエンドポイントとして公開するためのSwaggerオブジェクトモデルとミドルウェア。

- Swashbuckle.AspNetCore.SwaggerGen：
SwaggerDocumentルート、コントローラー、およびモデルから直接オブジェクトを構築するSwaggerジェネレーター。通常、Swaggerエンドポイントミドルウェアと組み合わせて、SwaggerJSONを自動的に公開します。

- Swashbuckle.AspNetCore.SwaggerUI：
SwaggerUIツールの埋め込みバージョン。Swagger JSONを解釈して、WebAPI機能を記述するための豊富でカスタマイズ可能なエクスペリエンスを構築します。これには、パブリックメソッド用の組み込みテストハーネスが含まれています。
