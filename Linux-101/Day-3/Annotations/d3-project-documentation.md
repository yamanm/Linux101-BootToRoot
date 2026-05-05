### Project 1.1: Kurumsal Dokümantasyon Rehberi

#### 1.1.1 Dokümantasyonun Amacı

Profesyonel dokümantasyonun amacı yalnızca bir sistemi açıklamak değildir. İyi hazırlanmış bir doküman, okuyucunun projeyi anlamasını, sistemi doğru kurmasını, operasyonel süreçleri güvenli biçimde yürütmesini ve gerektiğinde projeye katkı sunmasını kolaylaştırır.

Dokümantasyon aşağıdaki ihtiyaçlara cevap vermelidir:

- Kullanıcının sistemi hızlı anlamasını sağlamak
- Kurulum ve ilk kullanım süresini azaltmak
- Operasyonel hata oranını düşürmek
- Bakım süreçlerini standartlaştırmak
- Katkı süreçlerini yönetilebilir hale getirmek
- Güvenlik ve uyumluluk gereksinimlerini görünür kılmak
- Projenin uzun vadeli sürdürülebilirliğini desteklemek

Bu nedenle dokümantasyon, projenin yanında duran yardımcı bir metin olarak görülmemelidir. Doğru tasarlandığında dokümantasyon, projenin operasyonel parçalarından biri haline gelir.

---

#### 1.1.2 Hedef Kitle Analizi

Her doküman aynı okuyucuya hitap etmez. Bir README dosyasını ilk kez projeyi inceleyen kullanıcı okuyabilir. Bir operasyon dokümanını ise sistemi kuracak, izleyecek veya arıza anında müdahale edecek ekip kullanır. Bu nedenle dokümantasyon hazırlanmadan önce hedef kitle netleştirilmelidir.

| Hedef Kitle           | Temel İhtiyaç                          | Gerekli Doküman Türü                      |
| --------------------- | -------------------------------------- | ----------------------------------------- |
| Yeni kullanıcı        | Projeyi hızlı anlamak                  | README, Quick Start                       |
| Sistem yöneticisi     | Kurmak, izlemek, sorun gidermek        | Installation, Configuration, Operations   |
| Geliştirici           | Kod yapısını ve katkı sürecini anlamak | Architecture, API, CONTRIBUTING           |
| Güvenlik ekibi        | Riskleri ve kontrolleri görmek         | Security, Hardening, Vulnerability Policy |
| Maintainer            | Katkıları ve release sürecini yönetmek | Governance, Release Notes, Changelog      |
| Kurumsal karar verici | Projenin kapsamını ve değerini anlamak | Overview, Roadmap, Comparison             |

Hedef kitle doğru belirlenmezse doküman ya gereğinden fazla teknik kalır ya da teknik ekiplerin ihtiyaç duyduğu ayrıntıları karşılamaz.

---

#### 1.1.3 Dokümantasyon Katmanları ve Kullanım Amaçları

Kurumsal seviyede dokümantasyon tek bir README dosyasından oluşmaz. Projenin kullanım amacına, hedef kitlesine ve operasyonel gereksinimlerine göre farklı dokümantasyon katmanları hazırlanmalıdır.

**Katman 1: Projeye Giriş ve İlk Yönlendirme**

Bu bölüm, projeyle ilk kez karşılaşan okuyucunun hızlı biçimde yön bulmasını sağlar. Okuyucu bu aşamada projenin ne yaptığını, hangi problemi çözdüğünü ve ilk çalıştırma adımlarına nereden başlayacağını anlamalıdır.

İçermesi gerekenler:

- README
- Project overview
- Problem statement
- Core features
- Supported platforms
- Quick start
- Documentation index

README şu sorulara hızlı cevap vermelidir:

- Bu proje nedir?
- Hangi problemi çözer?
- Kimler kullanmalıdır?
- Nasıl kurulur?
- İlk örnek nasıl çalıştırılır?
- Daha detaylı bilgi nerede bulunur?

README, projenin giriş kapısıdır. Bu dosya dağınık, eksik veya belirsiz hazırlanırsa okuyucu daha detaylı dokümanlara geçmeden projeden uzaklaşabilir.

---

**Katman 2: Kurulum, Yapılandırma ve İlk Kullanım**

Bu bölüm, kullanıcıyı projeyi inceleme aşamasından çalışan bir sisteme taşımalıdır. Kurulum adımları açık, test edilmiş ve hedef platformla uyumlu olmalıdır.

İçermesi gerekenler:

- Requirements
- Installation
- Configuration
- First run
- Verification
- Usage examples

Kurulum dokümanı tahmine dayalı yazılmamalıdır. Komutların hangi işletim sistemi, dağıtım, sürüm veya çalışma ortamı için geçerli olduğu açıkça belirtilmelidir. Bağımlılıklar, servis gereksinimleri, paketler ve doğrulama adımları net olmalıdır.

---

**Katman 3: Operasyon ve Bakım Dokümantasyonu**

Linux ve sistem projelerinde operasyon dokümantasyonu doğrudan günlük kullanım kalitesini etkiler. Proje geliştirici açısından anlaşılır olabilir, ancak sistem yöneticisi sistemi nasıl izleyeceğini, nasıl yedekleyeceğini veya hata anında hangi adımları uygulayacağını bilmiyorsa dokümantasyon eksik kalır.

İçermesi gerekenler:

- Service management
- Logging
- Monitoring
- Backup
- Restore
- Troubleshooting
- Maintenance tasks

Bu bölüm özellikle production ortamları için önemlidir. Servislerin nasıl başlatılacağı, logların nereden okunacağı, izleme metriklerinin nasıl değerlendirileceği ve bakım işlemlerinin hangi sırayla yapılacağı açık biçimde yazılmalıdır.

---

**Katman 4: Mimari ve Mühendislik Dokümantasyonu**

Mimari ve mühendislik dokümantasyonu, projeyi geliştiren veya genişleten teknik ekipler için hazırlanır. Bu bölüm, yalnızca kodun nerede durduğunu değil, sistemin neden o şekilde tasarlandığını da açıklamalıdır.

İçermesi gerekenler:

- Architecture
- Codebase structure
- API documentation
- Data flow
- Design decisions
- ADR kayıtları
- Test strategy

Bu dokümanlar, yeni geliştiricilerin projeye daha hızlı dahil olmasını sağlar. Ayrıca tasarım kararlarının kayıt altına alınması, ileride yapılacak değişikliklerde bağlam kaybını azaltır.

---

**Katman 5: Yönetim Dokümantasyonu**

Açık kaynak veya ekip bazlı projelerde katkı sürecinin yönetilebilir olması gerekir. Bunun için yalnızca teknik açıklamalar yeterli değildir. Katkı kuralları, inceleme süreci, güvenlik bildirimi ve release yönetimi açıkça tanımlanmalıdır.

İçermesi gerekenler:

- CONTRIBUTING.md
- CODE_OF_CONDUCT.md
- SECURITY.md
- LICENSE
- Maintainer policy
- Branch strategy
- Review policy
- Release process

Bu bölüm, projenin nasıl yönetildiğini görünür hale getirir. Özellikle birden fazla kişinin katkı sunduğu projelerde belirsizliği azaltır ve bakım sürecini daha sürdürülebilir hale getirir.

---

**Katman 6: Güvenlik, Risk ve Sertleştirme Dokümantasyonu**

Birçok projede güvenlik dokümantasyonu ya eksik bırakılır ya da yalnızca genel uyarılarla sınırlı kalır. Oysa sistem, ağ, cloud, firewall ve security odaklı projelerde güvenlik bölümü ayrı bir dokümantasyon katmanı olarak ele alınmalıdır.

İçermesi gerekenler:

- Threat model
- Authentication
- Authorization
- Secret handling
- Dependency scanning
- Vulnerability reporting
- Secure configuration
- Hardening recommendations

Bu bölüm, projenin hangi tehditleri dikkate aldığını, hangi güvenlik kontrollerini kullandığını ve güvenli yapılandırmanın nasıl yapılacağını açıklamalıdır. Ayrıca hassas bilgilerin nasıl saklanacağı, bağımlılık risklerinin nasıl izleneceği ve güvenlik açığı bildirimlerinin nasıl yapılacağı da net olmalıdır.

---

**Katman 7: Olay Yönetimi ve Runbook Dokümantasyonu**

Enterprise ortamlarda olay yönetimi dokümantasyonu, arıza anında ekiplerin aynı prosedür üzerinden hareket etmesini sağlar. Bu dokümanlar, özellikle servis kesintisi, performans düşüşü, veri kaybı riski veya güvenlik olayı gibi durumlarda operasyonel değer üretir.

İçermesi gerekenler:

- Runbooks
- Incident response process
- Escalation path
- Recovery procedures
- Postmortem template
- Known issues
- Service degradation scenarios

Bu bölüm özellikle Linux, firewall, monitoring, backup, cloud ve security projelerinde önemlidir. Bir sorun oluştuğunda kimin ne yapacağı, hangi kontrollerin uygulanacağı ve olay sonrasında hangi değerlendirme adımlarının izleneceği önceden tanımlanmalıdır.

---

#### 1.1.4 Yazım Standartları

İyi dokümantasyon yalnızca doğru bilgi içermez. Aynı zamanda okunabilir, takip edilebilir ve uygulanabilir olmalıdır. Bu nedenle teknik doğruluk kadar yazım standardı da önemlidir.

**Netlik**

Cümleler kısa ve doğrudan olmalıdır. Her paragraf tek ana fikri taşımalıdır. Terimler belge boyunca tutarlı kullanılmalıdır.

Örneğin aynı kavram için bir yerde “servis”, başka bir yerde “hizmet”, başka bir yerde “daemon” kullanılıyorsa okuyucu bunun aynı şeyi mi yoksa farklı bileşenleri mi ifade ettiğini anlamakta zorlanabilir.

---

**Aktif Dil**

Edilgen yapı gereksiz yere artırılmamalıdır. Özellikle talimat içeren bölümlerde aktif dil daha anlaşılırdır.

```text
Servis yapılandırması tamamlandıktan sonra başlatılmalıdır. Yerine ↓
```

```text
Yapılandırmayı tamamladıktan sonra servisi başlatın.
```

Aktif dil, okuyucunun hangi işlemi yapması gerektiğini daha hızlı anlamasını sağlar.

---

**Kapsam**

Her dokümanın başında kapsam belirtilmelidir. Kapsam bölümü, okuyucunun dokümandan ne beklemesi gerektiğini netleştirir.

Aşağıdaki sorulara cevap verilmelidir:

- Bu doküman neyi açıklar?
- Neyi açıklamaz?
- Hangi ön koşullar gerekir?
- Hangi hedef kitleye yöneliktir?

Kapsam açık değilse doküman doğru bilgi içerse bile okuyucunun ihtiyacını karşılamayabilir.

---

**Liste ve Tablo Kullanımı**

Liste, sıralı işlem veya kontrol maddesi varsa kullanılmalıdır. Tablo ise karşılaştırma, parametre açıklaması veya hedef kitle ayrımı gibi durumlarda daha uygundur.

Liste ve tablo kullanımı belgeyi sadeleştirir; ancak her açıklamanın listeye dönüştürülmesi metni fazla mekanik hale getirebilir. Bu nedenle açıklama gerektiren yerlerde kısa paragraflar korunmalıdır.

---

**Örnekler**

Örnekler çalışabilir olmalıdır. Eksik, sahte veya test edilmemiş komutlar dokümana olan güveni azaltır.

Bir örnek veriliyorsa mümkün olduğunda şu bilgiler de sağlanmalıdır:

- Komutun hangi ortamda çalıştığı
- Beklenen çıktı
- Hata alınırsa kontrol edilecek noktalar
- Sürüm veya dağıtım bağımlılığı

---

#### 1.1.5 Erişilebilirlik Standardı

Dokümantasyon yalnızca teknik olarak doğru değil, erişilebilir de olmalıdır. Okuyucunun kullandığı cihaz, ekran okuyucu, renk algısı veya teknik seviyesi dokümanı takip etmesini engellememelidir.

**Gerekli İlkeler**

- Görseller için açıklayıcı alt text yazılmalı
- Diyagramlar yalnızca renk farkına dayanmamalı
- Başlık hiyerarşisi doğru kurulmalı
- Kod blokları dil etiketiyle verilmelidir
- Karmaşık görseller metinle desteklenmelidir

Erişilebilirlik, yalnızca engelli kullanıcılar için düşünülmemelidir. İyi yapılandırılmış başlıklar, açıklayıcı görseller ve doğru etiketlenmiş kod blokları tüm okuyucular için daha iyi bir okuma deneyimi sağlar.

---

#### 1.1.6 Hata Mesajı Dokümantasyonu

İyi hata mesajı yalnızca hatanın adını söylemez. Okuyucuya sorunun neden oluşmuş olabileceğini ve hangi adımlarla çözülebileceğini de göstermelidir.

Bir hata açıklaması iki temel soruya cevap vermelidir:

- Ne yanlış gitti?
- Kullanıcı bunu nasıl düzeltebilir?

**Örnek Yapı**

```text
Error:
Database connection timeout.

Cause:
The application could not connect to the database within the configured timeout.

Resolution:
1. Verify that the database service is running.
2. Check network connectivity.
3. Validate database credentials.
4. Increase the timeout value if the database is under heavy load.
```

Bu yapı, özellikle troubleshooting ve operations dokümanlarında standart hale getirilebilir. Böylece farklı hatalar aynı formatla açıklanır ve okuyucu çözüm adımlarını daha hızlı takip eder.

---

#### 1.1.7 Açık Kaynak Projeler İçin Minimum Dosya Seti

Bir açık kaynak veya GitHub tabanlı teknik proje, yalnızca kaynak koddan oluşmamalıdır. Kullanıcıların projeyi anlaması, katkı sunması, güvenlik açığı bildirmesi ve değişiklik geçmişini takip etmesi için belirli temel dosyalar bulunmalıdır.

Minimum yapı:

```text
README.md
LICENSE
CONTRIBUTING.md
CODE_OF_CONDUCT.md
SECURITY.md
CHANGELOG.md
docs/
examples/
```

Bu yapı, küçük ve orta ölçekli projeler için başlangıç standardı olarak kullanılabilir.

**Daha Olgun Yapı**

Daha kapsamlı projelerde dokümantasyon tek bir `docs/` klasörü altında konu bazlı ayrılmalıdır.

```text
docs/
├── getting-started/
├── installation/
├── configuration/
├── operations/
├── architecture/
├── security/
├── troubleshooting/
├── releases/
├── api/
└── runbooks/
```

Bu ayrım, okuyucunun ihtiyacı olan bilgiye daha hızlı ulaşmasını sağlar. Ayrıca proje büyüdükçe dokümantasyonun yönetilmesini kolaylaştırır.

---

#### 1.1.8 Katkı ve Maintainer Yönetimi

Katkı süreci açıkça yazılmamış projelerde issue, pull request ve review süreçleri zamanla dağınık hale gelir. Bu nedenle `CONTRIBUTING.md` dosyası yalnızca nezaket metni olarak değil, katkı sürecinin operasyonel rehberi olarak hazırlanmalıdır.

**CONTRIBUTING.md İçeriği**

- Nasıl issue açılır?
- Nasıl pull request gönderilir?
- Test zorunluluğu var mı?
- Commit standardı nedir?
- Kod inceleme süreci nasıl işler?
- Hangi katkılar kabul edilir?
- Hangi katkılar proje kapsamı dışındadır?

Maintainer tarafında ise branch stratejisi, release süreci ve review politikası net olmalıdır. Bu bilgiler belirsiz kalırsa katkı süreci kişisel tercihlere bağlı ilerler ve proje büyüdükçe sürdürülebilirlik zayıflar.

---

#### 1.1.9 Stil Rehberi

Stil rehberi, dokümantasyonun farklı kişiler tarafından yazılsa bile tutarlı kalmasını sağlar. Özellikle uzun soluklu eğitim serileri, açık kaynak projeler ve çoklu repository yapılarında stil standardı önemlidir.

**Minimum Stil Kuralları**

- Terimleri tutarlı kullan
- Başlıkları eylem veya konu odaklı yaz
- Gereksiz pazarlama dilinden kaçın
- Emoji kullanımını sınırla veya tamamen kaldır
- Komutları test etmeden yayınlama
- Kod bloklarında dil belirt
- Görselleri metinle açıkla
- Versiyon bağımlı bilgileri açıkça işaretle

Stil rehberi, yazarı kısıtlamak için değil, okuyucunun belge boyunca aynı kalite ve anlatım düzeniyle karşılaşmasını sağlamak için kullanılır.

---

#### 1.1.10 Kalite Kontrol Listesi

Dokümantasyon yayınlanmadan önce içerik, yapı, teknik doğruluk, dil ve güvenlik açısından kontrol edilmelidir. Aşağıdaki kontrol listesi, yayın öncesi son gözden geçirme için kullanılabilir.

**İçerik Kontrolü**

- Projenin amacı açık mı?
- Hedef kitle belli mi?
- Ön koşullar yazılmış mı?
- Kurulum adımları test edilmiş mi?
- Komutlar çalışıyor mu?
- Beklenen çıktılar verilmiş mi?
- Troubleshooting bölümü var mı?

---

**Yapı Kontrolü**

- Başlık hiyerarşisi doğru mu?
- README dokümantasyon indeksine bağlanıyor mu?
- İç bağlantılar çalışıyor mu?
- Gereksiz tekrar var mı?
- Uzun dokümanlar bölümlere ayrılmış mı?

---

**Teknik Kontrol**

- Sürüm bilgileri güncel mi?
- Komutlar hedef dağıtımla uyumlu mu?
- Dosya yolları doğru mu?
- Servis adları doğru mu?
- Güvenlik uyarıları eksik mi?

---

**Dil Kontrolü**

- Cümleler kısa mı?
- Etken dil kullanılmış mı?
- Terimler tutarlı mı?
- Gereksiz akademik ifade var mı?
- Blog dili veya pazarlama dili azaltılmış mı?

---

**Güvenlik Kontrolü**

- Secret veya credential örneği sızdırılmamış mı?
- Güvenlik bildirimi var mı?
- Dependency riskleri açıklanmış mı?
- Varsayılan yapılandırma güvenli mi?
- Yetkilendirme modeli belirtilmiş mi?

Bu kontrol listesi her doküman türü için bire bir aynı uygulanmak zorunda değildir. Ancak README, installation, operations, security ve troubleshooting gibi temel belgelerde bu başlıkların büyük bölümü gözden geçirilmelidir.

---

#### 1.1.11 Linux/System/Security İçin Önerilen Standart

Linux, system administration, security, cloud ve infrastructure odaklı dokümantasyonlarda yapı yalnızca konulara göre değil, operasyonel kullanım biçimine göre de tasarlanmalıdır. Okuyucu bir konuyu öğrenmek, uygulamak, doğrulamak ve sorun gidermek için aynı dokümantasyon seti içinde ilerleyebilmelidir.

**Repository Yapısı**

```text
README.md
LICENSE
CHANGELOG.md
CONTRIBUTING.md
SECURITY.md
docs/
├── 00-overview/
├── 01-getting-started/
├── 02-installation/
├── 03-configuration/
├── 04-operations/
├── 05-security/
├── 06-troubleshooting/
├── 07-projects/
├── 08-runbooks/
└── 09-references/
```

Bu yapı, hem eğitim odaklı hem de operasyon odaklı projelerde kullanılabilir. `overview` bölümü genel yönlendirme sağlar. `getting-started`, `installation` ve `configuration` bölümleri kullanıcının sistemi ayağa kaldırmasına yardım eder. `operations`, `security`, `troubleshooting` ve `runbooks` bölümleri ise sistemin uzun vadeli yönetimini destekler.

**Teknik Konu Şablonu**

```markdown
### Project X.X: Topic Title

#### X.X.X Purpose

#### X.X.X Scope

#### X.X.X Prerequisites

#### X.X.X Conceptual Explanation

#### X.X.X Technical Architecture

#### X.X.X Implementation Steps

#### X.X.X Verification

#### X.X.X Troubleshooting

#### X.X.X Security Considerations

#### X.X.X Operational Notes

#### X.X.X Best Practices

#### X.X.X Summary
```

Bu şablon, teknik konuların yalnızca teorik açıklamayla sınırlı kalmasını önler. Her konu; amaç, kapsam, ön koşul, mimari, uygulama, doğrulama, troubleshooting ve güvenlik boyutlarıyla ele alınır.

---

#### 1.1.12 Sonuç ve Uygulanabilir Standart

Kurumsal dokümantasyon, yalnızca bilgi aktarımı için hazırlanan yardımcı bir içerik değildir. İyi tasarlanmış bir dokümantasyon yapısı; kurulumu hızlandırır, operasyonel hataları azaltır, güvenlik gereksinimlerini görünür kılar ve projenin sürdürülebilirliğini güçlendirir.

Bu rehberde kullanılan yaklaşım, dört temel kaynağın birlikte değerlendirilmesine dayanır:

- Linux Foundation: güvenlik, açık kaynak yönetişimi ve sürdürülebilir proje yönetimi
- Write the Docs: dokümantasyon disiplini ve okuyucu odaklı yazım
- Open Source Guides: contributor süreçleri ve açık kaynak proje yönetimi
- Google Technical Writing: netlik, teknik yazım standardı ve okunabilirlik

Bu kaynaklar birlikte değerlendirildiğinde uygulanabilir bir dokümantasyon standardı ortaya çıkar. Bu standart; README dosyasından operasyon dokümanlarına, güvenlik rehberinden runbook yapısına kadar projenin tüm yaşam döngüsünü desteklemelidir.

Linux, system administration, security, cloud ve infrastructure projelerinde dokümantasyon yalnızca “nasıl yapılır” sorusuna cevap vermemelidir. Aynı zamanda “neden bu şekilde yapılır”, “nasıl doğrulanır”, “hata alınırsa ne kontrol edilir” ve “güvenli kullanım için nelere dikkat edilir” sorularını da karşılamalıdır.

Bu bakış açısı, dokümantasyonu statik bir metin olmaktan çıkarır ve projenin yönetilebilir, öğretilebilir ve sürdürülebilir bir parçası haline getirir.
