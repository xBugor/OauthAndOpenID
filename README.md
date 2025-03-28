# Oauth
Muhtemelen sosyal medya hesabınızı kullanarak giriş yapmanıza izin veren sitelerle karşılaşmışsınızdır. Bu özelliğin,  OAuth 2.0  kullanılarak oluşturulmuş olma ihtimali yüksektir.

* web sitelerinin ve web uygulamalarının başka bir uygulamadaki bir kullanıcının hesabına sınırlı erişim talep etmesini sağlayan yaygın olarak kullanılan bir yetkilendirme çerçevesidir. 

*  kullanıcı adı ve şifre paylaşmadan bir uygulamanın başka bir uygulamaya güvenli bir şekilde erişim izni vermesini sağlayan yetkilendirme protokolüdür.

* Örneğin, "Google ile Giriş Yap" veya "Discord ile Bağlan" gibi işlemler OAuth 2.0 ile gerçekleştirilir.

* Kullanıcı şifresini doğrudan paylaşmaz, bunun yerine Access Token kullanılır.

#### ÖRNEK

```mermaid
sequenceDiagram
    participant Kullanıcı
    participant Forum
    participant Google
    participant OAuth as OAuth Sağlayıcısı

    Kullanıcı->>Forum: "Google ile Giriş Yap" seçeneğine tıklar
    Forum->>OAuth: Kullanıcıyı Google'a yönlendirir
    OAuth->>Google: Kimlik doğrulama isteği iletir
    Google->>Kullanıcı: "Bu uygulamaya yetki vermek istiyor musunuz?"
    Kullanıcı->>Google: Giriş yapar ve izin verir
    Google->>Forum: Authorization Code döner
    Forum->>Google: Authorization Code ile Access Token talep eder
    Google->>Forum: Access Token döner
    Forum->>Google: Kullanıcının bilgilerini talep eder
    Google->>Forum: Kullanıcının adı ve e-posta adresini döner
    Forum->>Kullanıcı: Kullanıcı bilgileriyle giriş işlemini tamamlar
```

▶️ Kullanıcı bir uygulamaya giriş yapmak ister → Örneğin, bir sitenin giriş  forumuna "Google ile Giriş Yap" seçeneği eklediniz.

▶️ Forum, OAuth sağlayıcısına yönlendirme yapar → Kullanıcı Google’a yönlendirilir.

▶️ Kullanıcı giriş yapar ve izin verir → Google, "Bu uygulamaya yetki vermek istiyor musunuz?" diye sorar.

▶️ Google, forum sitesine bir Authorization Code döner → Bu kod, tek kullanımlıktır ve kullanıcıyı temsil eder.

▶️ Forum, Authorization Code ile Google’dan Access Token alır → Sunucu tarafından yönetilir.

▶️ Forum, Access Token ile kullanıcının verilerine güvenli şekilde erişebilir → Örneğin, kullanıcının adını ve e-posta adresini alabilir.

🔹 Önemli: OAuth sadece yetkilendirme yapar, kimlik doğrulama için OpenID Connect (OIDC) kullanılır.

Gerçek OAuth sürecinin uygulanabileceği çok sayıda farklı yol vardır. Bunlar OAuth **"akışları"(flows)** veya **"hibe türleri"**(grant types) olarak bilinir. 
Her biri farklı karmaşıklık ve güvenlik hususları düzeylerine sahip birkaç farklı hibe türü vardır. 

OAuth 2.0 Akış (Flow) Türleri/ hibe türleri(grant types)

⭐ Authorization Code Flow (Yetkilendirme Kodu Akışı)

✅ En güvenli yöntemdir.

✅ Sunucu tarafında kimlik doğrulama yapılır, token istemciye doğrudan verilmez.

🔹 Nasıl Çalışır?

* Kullanıcıya, talep edilen erişime izin verip vermediği sorulur. 

* Eğer kullanıcı kabul ederse, istemci uygulamaya bir "yetkilendirme kodu" (authorization code) verilir.

* Daha sonra istemci uygulama, bu kodu OAuth hizmeti ile değiştirerek bir access token alır. 

* Bu erişim belirteci, API çağrıları yaparak ilgili kullanıcı verilerini almak için kullanılır.

* Güvenli bir kanal kurulur bu OAuth  ilk defa kurulunca

**Token sunucuda saklanır (güvenli).**





<img src="./assets/oauth-authorization-code-flow.jpg" alt="alt yazı" width="500">


[portswigger][2]



⭐ **2. Implicit Grant (Dolaylı Yetkilendirme Akışı)**

Önce bir authorization code (yetkilendirme kodu) alıp sonra bunu bir erişim belirteciyle değiştirmek yerine, istemci uygulaması erişim belirtecini kullanıcı onayını verdikten hemen sonra alır.

* Çok daha az güvenlidir.  
* Tüm iletişim tarayıcı yönlendirmeleri aracılığıyla gerçekleşir.-
* Authorization Code Flowda olduğu gibi güvenli bir arka kanal yoktur.

<img src="./assets/oauth-implicit-flow.jpg" alt="alt yazı" width="500">

[portswigger][2]


⭐ 3.**Proof Key for Code Exchange (PKCE**






[1]: https://www.researchgate.net/figure/Sequence-Diagram-of-Interaction-with-Our-OAuth2-authorization-RESTful-Feed-Sharing-Service_fig3_272823002

[2]: https://portswigger.net/web-security/oauth/grant-types

### KAYNAKÇA
----

* [Researchgate](https://www.researchgate.net/figure/Sequence-Diagram-of-Interaction-with-Our-OAuth2-authorization-RESTful-Feed-Sharing-Service_fig3_272823002)

* [frontegg](https://frontegg.com/blog/oauth-grant-types)



