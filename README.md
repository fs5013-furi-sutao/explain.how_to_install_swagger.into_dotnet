# ASP.NET Core アプリに Swagger を導入する方法
## Swagger とは
Swagger とは、RESTful API の作成を補助するオープンソースのフレームワークのこと。 また、このフレームワークにおいて標準化されているドキュメント仕様そのものを指す言葉でもある。

## Swashbuckle
ASP.NET Core で Swagger を使うには、Swashbuckle パッケージを使う。

Swashbuckle には、次の 3 つの主要コンポーネントがある。

- Swashbuckle.AspNetCore.Swagger：  
SwaggerDocument オブジェクトを JSON エンドポイントとして公開するための Swagger オブジェクトモデルとミドルウェア。

- Swashbuckle.AspNetCore.SwaggerGen：  
SwaggerDocument ルート、コントローラー、およびモデルから直接オブジェクトを構築する Swagger ジェネレータ。通常、Swagger エンドポイントミドルウェアと組み合わせて、SwaggerJSON を自動的に公開する。

- Swashbuckle.AspNetCore.SwaggerUI：  
SwaggerUI ツールの埋め込みバージョン。Swagger JSON を解釈して、WebAPI 機能を記述するための豊富でカスタマイズ可能なエクスペリエンスを構築する。これには、パブリックメソッド用の組み込みテストハーネスが含まれている。


