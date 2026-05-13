### Chapter 1.2: Kurumsal Dağıtım Kurulumu

#### 1.2.1 Kurulum Ortamları ve Sanallaştırma

Linux sistemlerinin kurulumu, hedeflenen kullanım senaryosuna göre farklı yöntemler ve farklı altyapı modelleri üzerinden yapılabilir. Modern IT ortamlarında kurulum, yalnızca bir işletim sistemini fiziksel diske yüklemekten ibaret değildir. Sanallaştırma, otomasyon, güvenlik politikaları, kaynak planlaması ve altyapı standardizasyonu bu kararın parçası haline gelir.

Bu bölümde Linux kurulum ortamları ve sanallaştırma yaklaşımları, pratik kullanım ve kurumsal sistem yönetimi perspektifiyle ele alınmaktadır.

**Kurulum Ortamı Seçiminin Etkileri**

Linux kurulum modeli, sistemin nerede ve hangi amaçla çalışacağına göre belirlenir. Kurulum doğrudan fiziksel donanım üzerine yapılabilir. Aynı sistem bir sanal makine içinde, bir bulut instance üzerinde veya daha sınırlı bir kullanım senaryosunda konteyner tabanlı bir ortamda da çalıştırılabilir.

Bu tercih; performans beklentisini, yönetim biçimini, maliyeti, yedekleme yaklaşımını ve ölçekleme stratejisini etkiler. Bu nedenle kurulum ortamı seçimi, yalnızca teknik bir tercih değil, aynı zamanda operasyonel bir tasarım kararıdır.

Kurulum ortamları genel olarak üç ana grupta değerlendirilebilir: fiziksel kurulumlar, sanal makine tabanlı kurulumlar ve bulut tabanlı kurulumlar. Konteyner yaklaşımı ise klasik işletim sistemi kurulumundan farklı bir model sunsa da modern Linux altyapılarında ayrıca değerlendirilmesi gereken bir çalışma biçimidir.

**Bare Metal Kurulumlar ve Kullanım Alanları**

Fiziksel kurulum, işletim sisteminin doğrudan donanım üzerine yüklenmesidir. Bu modelde işletim sistemi ile donanım arasında sanallaştırma katmanı bulunmaz. Linux sistemi CPU, bellek, disk ve ağ kaynaklarını doğrudan kullanır.

Bare metal kurulumlar özellikle yüksek performans, düşük gecikme veya donanıma doğrudan erişim gerektiren sistemlerde tercih edilir. Veritabanı sunucuları, yüksek performanslı hesaplama sistemleri, özel donanım kullanan uygulamalar ve yoğun I/O gerektiren servisler bu gruba örnek verilebilir.

Buna karşılık bu modelde kaynak esnekliği daha sınırlıdır. Yeni kaynak eklemek, sistemi taşımak veya ölçeklemek sanallaştırılmış ortamlara göre daha maliyetli olabilir. Bu nedenle bare metal tercih edilirken yalnızca performans değil, bakım ve büyüme maliyeti de hesaba katılmalıdır.

**Sanal Makine Kurulumları ve Hypervisor Katmanı**

Sanallaştırma teknolojileri, tek bir fiziksel donanım üzerinde birden fazla sanal makinenin çalışmasını sağlar. Bu modelde hypervisor adı verilen katman, fiziksel kaynakları sanal makineler arasında paylaştırır ve her sanal makineye izole bir çalışma ortamı sunar.

Hypervisor’lar genel olarak iki ana gruba ayrılır. Type 1 hypervisor’lar doğrudan fiziksel donanım üzerinde çalışır. VMware ESXi, Microsoft Hyper-V ve KVM bu modele örnek verilebilir. Type 2 hypervisor’lar ise mevcut bir işletim sistemi üzerinde çalışır. VirtualBox ve VMware Workstation bu yaklaşımın yaygın örnekleridir.

Sanal makineler; test, geliştirme, eğitim, sistem yönetimi ve kurumsal altyapı senaryolarında önemli avantajlar sunar. Snapshot alma, klonlama, hızlı provisioning ve kaynakları merkezi olarak yönetme gibi özellikler, sistem yöneticilerinin işini kolaylaştırır. Ayrıca her sanal makinenin ayrı bir işletim sistemi ortamı gibi davranması, izolasyon ihtiyacı olan senaryolarda güçlü bir avantajdır.

**Konteyner Yaklaşımı ve İzolasyon Sınırları**

Modern Linux altyapılarında sanallaştırma ile birlikte konteyner teknolojileri de yaygın biçimde kullanılır. Konteynerler, uygulamaların bağımlılıklarıyla birlikte paketlenmesini ve farklı ortamlarda daha tutarlı şekilde çalıştırılmasını sağlar.

Konteynerler, sanal makinelerden farklı olarak ayrı bir kernel çalıştırmaz. Host işletim sisteminin kernel’ini paylaşırlar ve işletim sistemi seviyesinde izolasyon kullanırlar. Bu nedenle sanal makinelere göre daha hafiftirler ve aynı donanım üzerinde daha yüksek uygulama yoğunluğu elde edilebilir.

Docker ve Kubernetes gibi platformlar, konteyner tabanlı yaklaşımın yaygınlaşmasında önemli rol oynamıştır. Ancak konteynerlerin izolasyon modeli sanal makinelerle aynı değildir. Tam işletim sistemi ayrımı sağlamadıkları için güvenlik, yetkilendirme, image güvenilirliği ve runtime izolasyonu dikkatle planlanmalıdır.

**Bulut Tabanlı Kurulumlar**

Bulut bilişim, Linux sistemlerinin devreye alınma biçimini ciddi biçimde değiştirmiştir. Fiziksel donanım hazırlamak yerine, sanal kaynaklar üzerinden kısa sürede yeni sistemler oluşturulabilir. AWS, Azure ve Google Cloud gibi platformlar, Linux tabanlı sunucuların dakikalar içinde çalışır hale gelmesini sağlar.

Bulut ortamlarında sistem kurulumları çoğu zaman manuel adımlar yerine şablonlar, image’lar ve Infrastructure as Code yaklaşımlarıyla yönetilir. Terraform, CloudFormation veya benzeri araçlarla aynı altyapı tekrar üretilebilir hale gelir. Bu yaklaşım, özellikle büyük ölçekli ortamlarda tutarlılığı artırır ve dağıtım süresini kısaltır.

Bulut tabanlı kurulumlar esneklik ve ölçeklenebilirlik açısından güçlü avantajlar sunar. Bununla birlikte maliyet yönetimi, erişim kontrolü, ağ güvenliği, disk şifreleme ve logging gibi konular baştan planlanmadığında bulut ortamı hızlıca karmaşık hale gelebilir.

**Manuel Kurulumdan Otomasyona Geçiş**

Linux kurulumları manuel olarak yapılabileceği gibi otomatik yöntemlerle de gerçekleştirilebilir. Manuel kurulumlar öğrenme süreçleri, küçük test ortamları veya tekil sistemler için yeterli olabilir. Ancak sistem sayısı arttıkça manuel kurulumlar tutarsızlık ve zaman kaybı üretmeye başlar.

RHEL tabanlı sistemlerde Kickstart, Debian tabanlı sistemlerde Preseed gibi araçlar standart kurulumların otomatik hale getirilmesini sağlar. Bu araçlarla disk bölümleme, paket seçimi, ağ ayarları, kullanıcı oluşturma ve kurulum sonrası komutlar önceden tanımlanabilir.

Otomasyon, insan hatasını azaltır ve sistemler arasında tutarlı bir başlangıç noktası oluşturur. Büyük veri merkezlerinde, eğitim laboratuvarlarında veya kurumsal sunucu ortamlarında bu yaklaşım operasyonel yükü ciddi biçimde azaltır.

**Kurumsal Perspektiften Değerlendirme**

Kurulum ortamı seçimi, organizasyonun teknik ihtiyacına ve operasyonel önceliklerine göre yapılmalıdır. Yüksek performans ve donanıma yakın çalışma gerektiren sistemlerde bare metal yaklaşımı öne çıkabilir. Esneklik, hızlı geri dönüş ve kaynak optimizasyonu istenen yapılarda sanallaştırma daha uygun olabilir. Hızlı ölçekleme ve servis bazlı dağıtım gerektiren ortamlarda ise bulut platformları güçlü bir seçenek sunar.

Konteyner teknolojileri, özellikle modern uygulama geliştirme ve mikroservis mimarilerinde ayrı bir konuma sahiptir. Ancak konteynerleri klasik sunucu kurulumunun birebir alternatifi gibi değerlendirmek doğru değildir. Her model kendi izolasyon, güvenlik, yönetim ve maliyet dinamikleriyle birlikte ele alınmalıdır.

**Genel Değerlendirme**

Kurulum ortamları ve sanallaştırma kararları, Linux sistemlerinin nasıl yönetileceğini uzun vadede belirler. Doğru model seçildiğinde sistem daha kolay ölçeklenir, daha tutarlı yönetilir ve operasyonel riskler azalır.

Bu bölümde ele alınan kavramlar; sistem kurulumu, otomasyon, altyapı yönetimi ve güvenlik yapılandırmaları için zemin hazırlar. Linux’un farklı çalışma ortamlarına uyum sağlayabilmesi, onu modern IT altyapılarında esnek ve güçlü bir platform haline getirir.

#### 1.2.2 Kurulum Medyası Hazırlığı

Linux sistem kurulumunun ilk adımlarından biri, güvenilir ve doğru hazırlanmış bir kurulum medyası oluşturmaktır. Kurulum medyası, işletim sisteminin hedef sisteme aktarılmasını sağlar. Bu aşamada yapılacak bir hata, kurulumun başarısız olmasına, sistemin yanlış yapılandırılmasına veya güvenlik risklerinin daha en başta sisteme taşınmasına neden olabilir.

Bu nedenle kurulum medyası hazırlığı yalnızca teknik bir ön hazırlık olarak görülmemelidir. Kaynağın doğrulanması, dosya bütünlüğünün kontrol edilmesi, boot uyumluluğu ve kurumsal standartlarla uyum bu aşamanın parçasıdır.

**ISO Tabanlı Kurulum Medyaları**

Linux kurulumları çoğunlukla ISO imaj dosyaları üzerinden yapılır. ISO dosyası, işletim sisteminin kurulum için ihtiyaç duyduğu dosyaları içeren disk imajıdır. Bu imaj USB belleğe, DVD medyaya veya ağ tabanlı kurulum altyapılarına aktarılabilir.

Günümüzde en yaygın kurulum ortamı USB belleklerdir. Taşınabilir olmaları, hızlı yazılabilmeleri ve tekrar kullanılabilmeleri nedeniyle pratik bir çözüm sunarlar. Modern sistemlerde optik sürücülerin giderek azalması da USB tabanlı kurulumu standart hale getirmiştir.

DVD veya optik medya geçmişte yaygın kullanılmış olsa da bugün daha çok legacy sistemlerde veya özel gereksinimlerde karşımıza çıkar. Ağ tabanlı kurulumlar ise fiziksel medya taşıma ihtiyacını ortadan kaldırır. PXE gibi yöntemlerle sistemler merkezi bir sunucudan boot edilerek kurulabilir.

**ISO İmajı Doğrulama ve Güvenilir Kaynak Kullanımı**

Kurulum güvenliği, kullanılan ISO imajının güvenilirliğiyle başlar. ISO dosyaları her zaman dağıtımın resmi web sitesinden veya güvenilir mirror kaynaklarından indirilmelidir. Rastgele kaynaklardan indirilen kurulum imajları, sistemin daha kurulum aşamasında riskli hale gelmesine neden olabilir.

İndirme işleminden sonra checksum doğrulaması yapılmalıdır. SHA256 veya SHA512 gibi hash algoritmaları, indirilen dosyanın bozulup bozulmadığını ve beklenen dosya ile aynı olup olmadığını kontrol etmek için kullanılır.

Bu kontrol özellikle kurumsal ortamlarda ihmal edilmemelidir. Doğrulanmamış bir ISO imajı, hatalı kurulumlara veya güvenilmeyen bileşenlerin sisteme dahil edilmesine yol açabilir.

**USB Kurulum Medyası Oluşturma**

USB üzerinden kurulum medyası hazırlamak için ISO imajının USB cihaza uygun şekilde yazılması gerekir. Bu işlem basit bir kopyalama işlemi değildir. ISO imajı, boot edilebilir disk yapısını oluşturacak biçimde düşük seviyede yazılmalıdır.

Linux ortamında bu işlem genellikle `dd` komutu ile yapılır. `dd`, ISO imajını byte seviyesinde hedef diske yazar. Yanlış hedef disk seçilirse veri kaybı yaşanabileceği için işlem öncesinde disk adı mutlaka kontrol edilmelidir.

Windows ortamında Rufus, balenaEtcher ve benzeri araçlar kullanılabilir. Bu araçlar grafik arayüz üzerinden çalıştığı için özellikle eğitim ve bireysel kullanım senaryolarında daha güvenli bir deneyim sunar.

**Boot Edilebilir Medya, BIOS ve UEFI Uyumluluğu**

Kurulum medyasının kullanılabilmesi için boot edilebilir olması gerekir. Boot edilebilir medya, sistem açılışı sırasında BIOS veya UEFI firmware tarafından tanınır ve Linux kurulum yükleyicisini başlatır.

Eski sistemlerde BIOS tabanlı boot yapısı kullanılırken, modern sistemlerde UEFI yaygındır. UEFI sistemlerde genellikle GPT partition yapısı ve EFI System Partition kullanılır. Bu nedenle kurulum medyası hazırlanırken hedef sistemin boot modu dikkate alınmalıdır.

Secure Boot aktif olan sistemlerde yalnızca imzalı boot loader’lar çalıştırılabilir. Bazı Linux dağıtımları Secure Boot ile uyumlu çalışırken, bazı özel imajlar veya özelleştirilmiş kurulum medyaları ek ayar gerektirebilir.

**Ağ Üzerinden Kurulum ve PXE Kullanımı**

Kurumsal ortamlarda fiziksel medya kullanımını azaltmak için PXE kullanılır. PXE, sistemlerin ağ üzerinden boot edilmesini ve kurulumun merkezi bir sunucudan başlatılmasını sağlar.

Bu model özellikle veri merkezlerinde, sınıf/lab ortamlarında ve çok sayıda sistemin aynı anda kurulması gereken yapılarda kullanışlıdır. PXE altyapısı DHCP, TFTP ve çoğu zaman HTTP/NFS gibi servislerle birlikte çalışır.

PXE yaklaşımı merkezi yönetim, otomasyon ve hızlı dağıtım avantajı sunar. Ancak doğru ağ segmentasyonu, güvenlik kontrolleri ve erişim sınırlandırmaları yapılmazsa yetkisiz sistemlerin kurulum altyapısına erişme riski oluşabilir.

**Kurulum Medyası Hazırlığında Best Practice Yaklaşımı**

Kurumsal ortamlarda kurulum medyaları kişisel tercihlere göre değil, standart prosedürlere göre hazırlanmalıdır. ISO dosyalarının merkezi bir repository üzerinden yönetilmesi, hash doğrulamalarının kayıt altına alınması ve kullanılan imajların versiyonlarının izlenmesi gerekir.

Production ortamlarında kullanılan imajlar yetkisiz değişikliklere karşı korunmalıdır. Kurulum medyalarının kim tarafından, ne zaman ve hangi ISO ile oluşturulduğu takip edilebilir olmalıdır.

Otomasyon araçlarıyla entegre çalışan kurulum medyaları, standart sistem kurulumları için daha güvenilir bir temel oluşturur. Böylece aynı rol için kurulan sistemler daha tutarlı başlangıç konfigürasyonuna sahip olur.

**Genel Değerlendirme**

Kurulum medyası hazırlığı, Linux kurulumunun güvenli ve kontrollü başlamasını sağlar. Doğru kaynaktan alınmış, doğrulanmış ve hedef sistemle uyumlu hazırlanmış bir medya, kurulum sürecindeki birçok hatayı daha baştan engeller.

Bu aşamanın dikkatli yönetilmesi, özellikle kurumsal altyapılarda standartizasyon, güvenlik ve operasyonel sürdürülebilirlik açısından önem taşır.

#### 1.2.3 Disk Bölümleme Stratejileri

Disk bölümleme, bir depolama aygıtının mantıksal parçalara ayrılarak farklı amaçlar için düzenlenmesidir. Linux sistemlerinde bu karar yalnızca kurulum ekranında yapılan teknik bir seçim değildir. Performans, güvenlik, veri bütünlüğü, yedekleme, log yönetimi ve uzun vadeli bakım süreçleri üzerinde doğrudan etkisi vardır.

İyi planlanmış bir disk bölümlendirme yaklaşımı, sistemin daha kontrollü yönetilmesini sağlar. Yanlış planlanmış bir yapı ise disk doluluğu, servis kesintisi veya veri yönetimi problemleri olarak geri dönebilir.

**Disk Bölümleme Kavramı**

Disk bölümleme, fiziksel bir diskin birden fazla partition olarak yapılandırılmasıdır. Her partition ayrı bir dosya sistemiyle formatlanabilir ve Linux dosya sistemi hiyerarşisi içinde farklı mount noktalarına bağlanabilir.

Linux’ta tüm dizinler kök dizin `/` altında birleşik bir hiyerarşi içinde görünür. Ancak bu dizinlerin arkasında farklı diskler, farklı partition’lar veya farklı logical volume’lar bulunabilir. Bu esneklik, sistem yöneticisine disk kullanımını daha kontrollü planlama imkanı verir.

**Partition Tablo Türleri: MBR ve GPT**

Disk bölümleme sürecinde partition tablosu, diskin nasıl organize edileceğini belirler. En yaygın iki yaklaşım MBR ve GPT’dir.

MBR, eski sistemlerde kullanılan geleneksel partition tablosudur. En fazla 2 TB disk boyutunu destekler ve primary partition sayısı açısından sınırlıdır. Bu sınırlamalar nedeniyle modern sunucu sistemlerinde genellikle tercih edilmez.

GPT, güncel sistemler için daha uygun bir partition tablosudur. Daha büyük diskleri destekler, çok sayıda partition oluşturulmasına izin verir ve yedekli tablo yapısıyla veri bütünlüğünü daha iyi korur. UEFI tabanlı sistemlerde GPT kullanımı standart kabul edilir.

**Temel Bölüm Türleri ve Kullanım Amaçları**

Linux sistemlerde disk bölümleri, kullanım amacına göre farklı mount noktalarına ayrılabilir. Bu ayrım, sistem bileşenlerini birbirinden izole etmeye ve disk kullanımını daha öngörülebilir hale getirmeye yardımcı olur.

Kök bölümü `/`, işletim sisteminin temel bileşenlerini içerir. Sistem çalışması için zorunlu olan dosyalar bu yapı altında bulunur.

`/home` bölümü kullanıcı verilerini barındırır. Bu alanın ayrı tutulması, sistem yeniden kurulumlarında veya işletim sistemi güncellemelerinde kullanıcı verilerinin daha kolay korunmasını sağlar.

`/var` bölümü log dosyaları, spool verileri, cache dosyaları ve dinamik sistem verileri için kullanılır. Log üretimi yoğun olan sistemlerde `/var` alanının ayrı tutulması, logların kök dosya sistemini doldurmasını engeller.

`/tmp` bölümü geçici dosyalar için kullanılır. Güvenlik veya performans gereksinimlerine bağlı olarak ayrı bir partition olarak yapılandırılabilir.

`/boot` bölümü sistemin açılışı için gereken kernel, initramfs ve boot loader bileşenlerini içerir. UEFI sistemlerde ayrıca EFI System Partition kullanılır.

Swap alanı, fiziksel belleğin yetersiz kaldığı durumlarda kullanılan disk alanıdır. Swap, RAM’in yerini performans açısından tutmaz; ancak bellek baskısı altında sistemin daha kontrollü davranmasına yardımcı olabilir.

**LVM ile Esnek Disk Yönetimi**

Modern Linux sistemlerde disk yönetimini daha esnek hale getirmek için LVM kullanılır. LVM, fiziksel diskleri ve partition’ları mantıksal hacimler halinde yönetmeye imkan verir.

LVM sayesinde disk alanı sonradan genişletilebilir, farklı logical volume’lar arasında yeniden planlama yapılabilir ve bazı senaryolarda snapshot alınabilir. Bu özellikler özellikle kurumsal ortamlarda disk planlamasını daha esnek hale getirir.

Ancak LVM kullanımı planlama ihtiyacını ortadan kaldırmaz. Hangi volume’un ne kadar büyüyebileceği, hangi dosya sisteminin kullanılacağı ve yedekleme stratejisinin nasıl işleyeceği baştan düşünülmelidir.

**RAID ve Veri Dayanıklılığı**

Disk bölümleme stratejileri veri güvenliğiyle de ilişkilidir. RAID teknolojileri, birden fazla diski birlikte kullanarak dayanıklılık veya performans avantajı sağlar.

RAID 1 diskler arasında aynalama yapar ve disk arızalarına karşı veri sürekliliği sağlar. RAID 5, RAID 10 gibi yapılandırmalar ise farklı seviyelerde performans ve dayanıklılık dengesi sunar. Linux sistemlerde hem donanımsal RAID hem de yazılımsal RAID çözümleri kullanılabilir.

RAID, yedekleme çözümü değildir. Disk arızasına karşı koruma sağlayabilir; ancak yanlış silme, dosya bozulması, fidye yazılımı veya uygulama hatası gibi durumlarda ayrı bir backup stratejisi gerekir.

**Sistem Rolüne Göre Bölümleme Planı**

Kurumsal sistemlerde disk bölümleme, sistemin rolüne göre planlanmalıdır. Bir veritabanı sunucusu, web sunucusu, log sunucusu veya dosya sunucusu aynı disk düzenine ihtiyaç duymaz.

Log yoğunluğu yüksek sistemlerde `/var` ayrı bir disk veya volume üzerinde tutulabilir. Veritabanı sistemlerinde veri dizinleri için ayrı disk grupları planlanabilir. Kullanıcı verisi barındıran sistemlerde `/home` veya uygulama veri dizinleri ayrı yönetilebilir.

Güvenlik açısından bazı dizinlerin ayrı partition olarak yapılandırılması ek kontrol imkanı sunar. Örneğin belirli mount seçenekleriyle çalıştırma izinleri sınırlandırılabilir veya geçici dosya alanları daha kontrollü hale getirilebilir.

**Genel Değerlendirme**

Disk bölümleme stratejisi, Linux sistem kurulumunun en dikkatli planlanması gereken alanlarından biridir. Doğru yapılandırılmış bir disk planı, sistemin daha güvenli, daha yönetilebilir ve daha sürdürülebilir çalışmasına katkı sağlar.

GPT, LVM ve RAID gibi teknolojiler birlikte değerlendirildiğinde Linux sistemlerde esnek ve dayanıklı depolama tasarımları oluşturulabilir. Bu bölümdeki kavramlar, dosya sistemleri, performans optimizasyonu, yedekleme ve sistem yönetimi konuları için temel oluşturur.

#### 1.2.4 Minimal vs Full Kurulumlar

Linux kurulumu sırasında verilmesi gereken önemli kararlardan biri, sistemin minimal kurulumla mı yoksa full kurulum modeliyle mi hazırlanacağıdır. Bu karar, yalnızca kurulumda yüklenecek paket sayısını belirlemez. Güvenlik yüzeyini, kaynak kullanımını, bakım yükünü ve sistemin uzun vadeli yönetim biçimini de etkiler.

Bu bölümde minimal ve full kurulum yaklaşımları teknik ve kurumsal kullanım açısından değerlendirilmektedir.

**Minimal Kurulum Yaklaşımı**

Minimal kurulum, işletim sisteminin çalışması için gerekli olan çekirdek bileşenlerin ve temel araçların yüklendiği sade bir kurulum modelidir. Bu yaklaşımda grafik arayüzler, ek servisler, geliştirme araçları ve yardımcı paketler varsayılan olarak kurulmaz.

Sistem yöneticisi ihtiyaç duyduğu paketleri sonradan kontrollü biçimde ekler. Böylece sistem yalnızca gerekli bileşenleri içerir ve daha temiz bir başlangıç noktası sunar.

Minimal kurulumun en güçlü avantajlarından biri güvenliktir. Daha az paket, daha dar saldırı yüzeyi anlamına gelir. Gereksiz servislerin çalışmaması da hem kaynak kullanımını azaltır hem de riskleri sınırlar.

Bu yaklaşım özellikle sunucu sistemleri, bulut instance’ları, konteyner host’ları ve güvenlik hassasiyeti yüksek altyapılar için uygundur. Temel prensip, sisteme yalnızca gerçekten ihtiyaç duyulan bileşenleri dahil etmektir.

**Full Kurulum Yaklaşımı**

Full kurulum, işletim sistemiyle birlikte geniş bir paket setinin yüklendiği modeldir. Masaüstü ortamları, yardımcı araçlar, geliştirme kütüphaneleri ve çeşitli servisler kurulumla birlikte hazır gelir.

Bu model kullanım kolaylığı sağlar. Sistem kurulumdan sonra daha hızlı kullanılabilir hale gelir ve özellikle masaüstü kullanıcıları, eğitim ortamları veya hızlı prototipleme çalışmaları için pratik olabilir.

Ancak full kurulum daha fazla disk alanı tüketir, daha fazla paket yönetimi gerektirir ve güvenlik yüzeyini genişletir. Sistemde ihtiyaç duyulmayan servislerin veya paketlerin bulunması, bakım süreçlerini de karmaşıklaştırabilir.

**Performans ve Kaynak Kullanımı**

Minimal kurulumlar daha az servisle çalıştığı için genellikle daha düşük bellek ve CPU tüketimine sahiptir. Bu durum özellikle sınırlı kaynaklara sahip sanal makinelerde, bulut ortamlarında ve yoğun sistemlerde avantaj sağlar.

Full kurulumlarda arka planda çalışan servisler, grafik bileşenler ve ek araçlar sistem yükünü artırabilir. Modern donanımlar bu yükü çoğu zaman tolere edebilir; ancak sunucu ortamlarında gereksiz kaynak tüketimi uzun vadede maliyet oluşturur.

Kurumsal sistemlerde performans kadar öngörülebilirlik de önemlidir. Minimal kurulumlar daha sade bir başlangıç noktası sunduğu için sistem davranışını analiz etmek ve optimize etmek daha kolaydır.

**Güvenlik Perspektifi**

Güvenlik açısından minimal kurulumlar genellikle daha avantajlıdır. Sistemde daha az yazılım bileşeni bulunduğu için potansiyel açıklık sayısı azalır. Gereksiz servislerin kapalı olması da dışarıdan erişilebilecek yüzeyi daraltır.

Full kurulumlarda ise daha fazla paket ve servis bulunduğu için düzenli güncelleme, servis kontrolü ve hardening çalışmaları daha fazla önem kazanır. Kullanılmayan paketlerin sistemde kalması, güvenlik ve bakım açısından gereksiz yük oluşturabilir.

Kurumsal güvenlik politikalarında yaygın yaklaşım, minimal kurulumla başlamak ve sistemi ihtiyaçlara göre kontrollü biçimde genişletmektir.

**Yönetilebilirlik ve Operasyonel Süreçler**

Minimal kurulumlar sistem yöneticisine daha fazla kontrol verir. Hangi paketlerin yükleneceği, hangi servislerin çalışacağı ve sistemin hangi role göre yapılandırılacağı açık biçimde belirlenir.

Bunun karşılığında başlangıç yapılandırması daha fazla uzmanlık gerektirir. Gerekli araçların manuel veya otomasyonla eklenmesi gerekir. Bu nedenle minimal kurulumlar, iyi hazırlanmış bir kurulum sonrası yapılandırma planıyla birlikte kullanılmalıdır.

Full kurulumlar hızlı başlangıç avantajı sağlar. Ancak gereksiz paketlerin ayıklanması, servislerin kapatılması ve sistemin sadeleştirilmesi ek iş yükü oluşturabilir.

Kurumsal ortamlarda en dengeli yaklaşım çoğu zaman minimal kurulum üzerine otomasyon uygulamaktır. Böylece hem sade bir sistem elde edilir hem de standart yapılandırma tekrarlanabilir hale gelir.

**Kullanım Senaryolarına Göre Tercih**

Minimal kurulumlar genellikle şu senaryolarda tercih edilir:

- Sunucu sistemleri
- Bulut altyapıları
- Konteyner platformları
- Güvenlik hassasiyeti yüksek ortamlar
- Otomasyonla yönetilen kurumsal sistemler

Full kurulumlar ise şu senaryolarda daha uygun olabilir:

- Masaüstü sistemler
- Eğitim ve laboratuvar ortamları
- Hızlı prototipleme çalışmaları
- Grafik arayüz gerektiren kullanıcı senaryoları

Bu ayrım, sistemin rolüne göre doğru kurulum modelinin seçilmesini kolaylaştırır.

**Genel Değerlendirme**

Minimal ve full kurulumlar farklı ihtiyaçlara cevap veren iki ayrı modeldir. Minimal kurulum güvenlik, performans ve kontrol açısından güçlü bir başlangıç sağlar. Full kurulum ise kullanım kolaylığı ve hızlı hazır hale gelme avantajı sunar.

Kurumsal Linux altyapılarında genellikle minimal kurulum tercih edilir ve sistemler ihtiyaçlara göre genişletilir. Bu yaklaşım, hem operasyonel standardizasyonu güçlendirir hem de sistemin daha sade ve yönetilebilir kalmasına yardımcı olur.

#### 1.2.5 Kurulum Sonrası Yapılandırma

Linux kurulumu tamamlandıktan sonra yapılan yapılandırmalar, sistemin gerçek kullanım ortamına hazırlanmasını sağlar. Varsayılan kurulumlar genel amaçlıdır ve çoğu zaman production standartlarını doğrudan karşılamaz. Bu nedenle kurulum sonrası adımlar sistemin rolüne, güvenlik gereksinimlerine ve kurumun operasyonel standartlarına göre planlanmalıdır.

Bu aşama; güncelleme, ağ yapılandırması, kullanıcı yönetimi, servis kontrolü, güvenlik sıkılaştırması, zaman senkronizasyonu, depolama ayarları ve otomasyon gibi birçok başlığı kapsar.

**İlk Güncelleme ve Paket Güvenliği**

Kurulum sonrası ilk yapılması gereken işlemlerden biri sistemi güncel hale getirmektir. ISO imajları kurulum anında güncel görünse bile zaman içinde yeni güvenlik yamaları ve paket güncellemeleri yayınlanmış olabilir.

Paket yöneticisi aracılığıyla sistemdeki paketler güncellenmeli ve güvenlik yamaları uygulanmalıdır. Bu işlem yalnızca yeni özellikler kazandırmaz; bilinen güvenlik açıklarının kapatılması açısından da gereklidir.

Production ortamlarında güncelleme süreci plansız yapılmamalıdır. Test, onay, bakım penceresi ve geri dönüş planı gibi adımlar kurumsal güncelleme politikasının parçası olmalıdır.

**Ağ Yapılandırması**

Sistemin ağ ayarları, erişilebilirlik ve servis sürekliliği açısından dikkatle yapılandırılmalıdır. IP adresi, gateway, DNS sunucuları, hostname ve network interface ayarları bu aşamada kontrol edilir.

Kurumsal ortamlarda sunucu sistemleri için çoğu zaman statik IP adresleri tercih edilir. Bu yaklaşım servis erişimini daha öngörülebilir hale getirir ve firewall, DNS, monitoring gibi bileşenlerin daha düzenli yönetilmesini sağlar.

Ağ yapılandırması yapılırken yalnızca bağlantının çalışması yeterli değildir. Firewall politikaları, erişim sınırları, DNS doğruluğu ve ağ segmentasyonu da birlikte değerlendirilmelidir.

**Kullanıcı ve Yetki Yönetimi**

Kurulum sonrası güvenlik yapılandırmasının önemli adımlarından biri kullanıcı ve yetki yönetimidir. Root erişimi kontrol altına alınmalı, sistem yönetimi için ayrı kullanıcı hesapları oluşturulmalı ve yetkilendirme sudo üzerinden yönetilmelidir.

`sudo` mekanizması, kullanıcıların belirli yönetim işlemlerini kontrollü biçimde yapmasını sağlar. Bu yaklaşım hem güvenliği artırır hem de yapılan işlemlerin izlenebilirliğini güçlendirir.

Güçlü parola politikaları uygulanmalı, gereksiz kullanıcı hesapları kaldırılmalı ve mümkün olan ortamlarda merkezi kimlik yönetimiyle entegrasyon değerlendirilmelidir.

**Gereksiz Servislerin Ayıklanması ve Paket Yönetimi**

Kurulumdan sonra sistemde çalışan servisler gözden geçirilmelidir. Minimal kurulumlarda servis sayısı daha sınırlı olurken, full kurulumlarda birçok servis varsayılan olarak aktif gelebilir.

Systemd üzerinden hangi servislerin çalıştığı, hangilerinin boot sırasında otomatik başladığı ve hangilerinin devre dışı bırakılması gerektiği kontrol edilmelidir. Gereksiz servislerin kapatılması hem kaynak kullanımını azaltır hem de güvenlik yüzeyini daraltır.

Ayrıca sistemin rolüne göre gerekli paketler kurulmalı, gereksiz paketler kaldırılmalı ve paket kaynakları güvenilir repository’lerle sınırlandırılmalıdır.

**Güvenlik Sertleştirme ve Erişim Kontrolleri**

Kurulum sonrası yapılandırmanın en hassas adımlarından biri sistem hardening çalışmasıdır. Amaç, sistemi varsayılan ayarlarla bırakmak yerine daha güvenli ve kontrollü bir çalışma durumuna getirmektir.

Firewall yapılandırması yapılmalı ve yalnızca gerekli portlar açık bırakılmalıdır. SELinux veya AppArmor gibi zorunlu erişim kontrol mekanizmaları devre dışı bırakılmadan önce mutlaka değerlendirilmelidir. Mümkün olan durumlarda bu mekanizmalar uygun policy ile aktif kullanılmalıdır.

SSH erişimi ayrıca sıkılaştırılmalıdır. Root login devre dışı bırakılmalı, anahtar tabanlı kimlik doğrulama tercih edilmeli ve erişim yalnızca gerekli kullanıcılarla sınırlandırılmalıdır. Loglama mekanizmaları da aktif ve izlenebilir durumda olmalıdır.

**Zaman, Bölge ve Locale Ayarları**

Sistem saatinin doğru olması, log kayıtları, sertifika doğrulamaları, dağıtık sistemler ve zaman bağımlı uygulamalar için önemlidir. NTP veya Chrony gibi servislerle sistem saati güvenilir kaynaklarla senkronize edilmelidir.

Zaman dilimi, sistemin bulunduğu operasyonel konuma göre ayarlanmalıdır. Locale ayarları ise dil, karakter seti ve uygulama davranışlarını etkileyebilir. Özellikle çok dilli veya uluslararası sistemlerde bu ayarlar baştan doğru planlanmalıdır.

**Depolama ve Dosya Sistemi Ayarları**

Kurulum sonrası disk ve dosya sistemi yapılandırması tekrar gözden geçirilmelidir. Mount noktaları, dosya sistemi seçenekleri, disk kotaları ve log/veri dizinlerinin konumu sistem rolüne göre kontrol edilmelidir.

LVM kullanılıyorsa volume büyüme stratejisi ve disk kapasite planı belirlenmelidir. Log yoğunluğu yüksek sistemlerde `/var`, uygulama verisi barındıran sistemlerde ilgili veri dizinleri ayrı volume veya disk üzerinde konumlandırılabilir.

Bu kontroller, ileride yaşanabilecek disk doluluğu, performans ve bakım problemlerini azaltır.

**Otomasyon ve Standartlaştırma**

Kurumsal ortamlarda kurulum sonrası yapılandırmaların manuel yapılması sürdürülebilir değildir. Sistem sayısı arttıkça manuel işlemler tutarsızlık üretir ve hata ihtimalini yükseltir.

Ansible, Puppet, Chef veya benzeri araçlar kullanılarak sistemler belirli bir konfigürasyon standardına göre yapılandırılabilir. Kullanıcılar, paketler, servisler, güvenlik ayarları ve dosya içerikleri otomasyonla yönetilebilir.

Bu yaklaşım, aynı rol için kurulan sistemlerin benzer şekilde davranmasını sağlar. Ayrıca değişikliklerin sürümlenmesi, denetlenmesi ve tekrar uygulanması daha kolay hale gelir.

**Genel Değerlendirme**

Kurulum sonrası yapılandırma, Linux sisteminin gerçek kullanım ortamına hazırlanmasını sağlayan aşamadır. Varsayılan kurulum, çoğu zaman yalnızca başlangıç noktasıdır. Sistemin güvenli, kararlı ve yönetilebilir hale gelmesi için ek yapılandırma gerekir.

Güncelleme, ağ ayarları, kullanıcı yönetimi, servis kontrolü, hardening, zaman senkronizasyonu, depolama planı ve otomasyon birlikte ele alındığında sistem daha tutarlı ve sürdürülebilir bir hale gelir. Bu yaklaşım, Linux sistemlerinin kurumsal ortamlarda güvenle işletilebilmesi için sağlam bir temel oluşturur.
