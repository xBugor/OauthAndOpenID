# Oauth
Muhtemelen sosyal medya hesabınızı kullanarak giriş yapmanıza izin veren sitelerle karşılaşmışsınızdır. Bu özelliğin,  OAuth 2.0  kullanılarak oluşturulmuş olma ihtimali yüksektir.

* web sitelerinin ve web uygulamalarının başka bir uygulamadaki bir kullanıcının hesabına sınırlı erişim talep etmesini sağlayan yaygın olarak kullanılan bir yetkilendirme çerçevesidir. 

*  kullanıcı adı ve şifre paylaşmadan bir uygulamanın başka bir uygulamaya güvenli bir şekilde erişim izni vermesini sağlayan yetkilendirme protokolüdür.

* Örneğin, "Google ile Giriş Yap" veya "Discord ile Bağlan" gibi işlemler OAuth 2.0 ile gerçekleştirilir.

* Kullanıcı şifresini doğrudan paylaşmaz, bunun yerine Access Token kullanılır.

#### ÖRNEK


OAuth 2.0'ın temel işleyişi şu adımlardan oluşur:

▶️ Kullanıcı bir uygulamaya giriş yapmak ister → Örneğin, bir sitenin giriş  forumuna "Google ile Giriş Yap" seçeneği eklediniz.

▶️ Forum, OAuth sağlayıcısına yönlendirme yapar → Kullanıcı Google’a yönlendirilir.

▶️ Kullanıcı giriş yapar ve izin verir → Google, "Bu uygulamaya yetki vermek istiyor musunuz?" diye sorar.

▶️ Google, forum sitesine bir Authorization Code döner → Bu kod, tek kullanımlıktır ve kullanıcıyı temsil eder.

▶️ Forum, Authorization Code ile Google’dan Access Token alır → Sunucu tarafından yönetilir.

▶️ Forum, Access Token ile kullanıcının verilerine güvenli şekilde erişebilir → Örneğin, kullanıcının adını ve e-posta adresini alabilir.

🔹 Önemli: OAuth sadece yetkilendirme yapar, kimlik doğrulama için OpenID Connect (OIDC) kullanılır.

Gerçek OAuth sürecinin uygulanabileceği çok sayıda farklı yol vardır. Bunlar OAuth "akışları"(flows) veya "hibe türleri"(grant types) olarak bilinir. 

OAuth 2.0 Akış (Flow) Türleri

1️⃣ Authorization Code Flow (Önerilen)

✅ En güvenli yöntemdir.

✅ Sunucu tarafında kimlik doğrulama yapılır, token istemciye doğrudan verilmez.

🔹 Nasıl Çalışır?

Kullanıcı giriş yapar → Yetkilendirme kodu alınır.

Yetkilendirme kodu ile Access Token talep edilir.

Token sunucuda saklanır (güvenli).

🔹 Kullanım Alanı: Web ve mobil uygulamalar.