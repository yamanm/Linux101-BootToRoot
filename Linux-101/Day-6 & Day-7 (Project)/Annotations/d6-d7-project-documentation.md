# Boot2Root Technologies Linux Sunucu Altyapısı Projesi

# 1 | Proje Senaryosu

Boot2Root Technologies, iç operasyonlarında kullanmak üzere yeni bir Linux sunucu altyapısı kurmak istemektedir. İlk aşamada şirket, test ortamı için birkaç Linux sunucusu hazırlayacak, daha sonra doğrulanan kurulum standardını production ortamına taşıyacaktır.

Şirket, yeni geliştirdiği yazılımın test ortamında çalıştırılabilmesi için gerekli bileşenleri ve temel yapılandırmaları içeren bir imaj dosyası hazırlamıştır. Bu yazılım confidential ve ticari nitelik taşıdığı için e-mail, genel dosya paylaşım servisleri veya kontrolsüz aktarım yöntemleriyle taşınmayacaktır.

Bu yazılımın ilerleyen aşamada production ortamında ve site-to-site bağlantı ile merkeze bağlı Bakü şubesindeki Linux sunucularda da kullanılması planlanmaktadır.

Site-to-site bağlantının network ekibi tarafından önceden kurulduğu varsayılacaktır. Bu proje kapsamında VPN kurulumu yapılmayacak, yalnızca Linux sunucuların bu güvenli bağlantı üzerinden erişilebilirliği, dosya aktarımına hazır hale getirilmesi ve aktarım sonrası bütünlük doğrulaması test edilecektir.

Bu proje kapsamında gerçek production imajı yerine, lab ortamında oluşturulacak 10 MB boyutunda bir test imaj dosyası kullanılacaktır. Böylece büyük dosya boyutuna sahip veri kullanılmadan, gerçek dosya aktarım süreci simüle edilecektir.

Yapılan teknik toplantılar sonucunda, bu senaryonun öncelikle test ortamında uygulanmasına, olası hataların giderilmesine ve başarılı doğrulama sonrasında aynı yaklaşımın production ortamına taşınmasına karar verilmiştir. Bu kapsamda senior ve junior sistem mühendislerine farklı seviyelerde görevler atanmıştır.

---

# 2 | Proje Amacı

Bu projenin amacı, yeni bir Linux sunucu altyapısının kurumsal standartlara uygun şekilde hazırlanmasını, test edilmesini ve dokümante edilmesini sağlamaktır.

Proje sonunda aşağıdaki konular uygulamalı olarak ele alınacaktır:

- Kurumsal Linux dağıtımı seçimi
- Sanal makine tabanlı Linux sunucu kurulumu
- ISO dosyası temini ve SHA256 doğrulaması
- Minimal ve full installation karşılaştırması
- Disk partition stratejisi
- Linux FHS yapısının operasyonel kullanımı
- Hostname, timezone, keyboard layout ve kullanıcı yapılandırması
- SSH erişimi ve temel network doğrulaması
- `dd + ssh` ile dosya aktarımı
- `sha256sum` ile bütünlük doğrulaması
- Post-installation kontrol yaklaşımı
- Junior ve senior sistem mühendisliği görev ayrımı
- Temel hata analizi ve troubleshooting yaklaşımı

---

# 3 | Proje Kapsamı

Bu proje kapsamında aşağıdaki işlemler yapılacaktır:

- Rocky Linux ve Debian sunucuları sanal makine olarak kurulacaktır.
- Rocky Linux sunucusu Ankara lokasyonunu temsil edecektir.
- Debian sunucusu Bakü şubesini temsil edecektir.
- ISO dosyaları SHA256 checksum ile doğrulanacaktır.
- Minimal ve full installation profilleri karşılaştırılacaktır.
- Test imaj dosyası kaynak sunucuda oluşturulacaktır.
- Test imaj dosyası `dd + ssh` yöntemiyle hedef sunucuya aktarılacaktır.
- Aktarım sonrası hedef sunucuda checksum doğrulaması yapılacaktır.
- Kurulum sonrası sistem, disk, network, servis ve log kontrolleri gerçekleştirilecektir.
- Tüm süreç teknik dokümantasyon haline getirilecektir.

---

# 4 | Kapsam Dışı Konular

Bu proje aşağıdaki konuları detaylı şekilde kapsamaz:

- Site-to-site VPN kurulumu
- IPsec veya WireGuard yapılandırması
- Gelişmiş firewall policy tasarımı
- SELinux policy yazımı
- Merkezi kimlik yönetimi
- Ansible otomasyonu
- Container image registry kullanımı
- CI/CD pipeline entegrasyonu
- Gerçek production deployment işlemi

Bu projede ana odak noktası Linux sunucu kurulum standardı, temel doğrulama, FHS farkındalığı, güvenli dosya aktarımı ve checksum tabanlı bütünlük kontrolüdür.

---

# 5 | Lab Topolojisi

| Sistem              | Dağıtım                                    | Rol                 | Lokasyon |
| ------------------- | ------------------------------------------ | ------------------- | -------- |
| `tr-rocky-min-01`   | Rocky Linux Minimal                        | Kaynak Linux sunucu | Ankara   |
| `az-debian-full-01` | Debian Full / Server with additional tools | Hedef Linux sunucu  | Bakü     |

---

# 6 | Örnek IP Planı

| Sistem              |       IP Adresi | Açıklama             |
| ------------------- | --------------: | -------------------- |
| `tr-rocky-min-01`   | `192.168.10.10` | Ankara kaynak sunucu |
| `az-debian-full-01` | `192.168.20.10` | Bakü hedef sunucu    |

Not: Gerçek site-to-site bağlantı kurulmayacaktır. Bu IP planı, iki farklı lokasyonu temsil eden test ağı varsayımıyla kullanılacaktır.

---

# 7 | Şirket Beklentileri

Boot2Root Technologies proje kapsamında aşağıdaki çıktıları beklemektedir:

- Kurumsal kullanıma uygun Linux dağıtımı seçilmelidir.
- Kurulum ortamı sanal makine üzerinde hazırlanmalıdır.
- ISO dosyaları doğru şekilde temin edilmeli ve doğrulanmalıdır.
- Sunucular için uygun disk partition stratejisi belirlenmelidir.
- Minimal ve full installation seçenekleri teknik olarak karşılaştırılmalıdır.
- Kurulum sonrası temel sistem kontrolleri yapılmalıdır.
- FHS yapısı incelenmeli ve sistem dizinlerinin rolü belgelenmelidir.
- Test imaj dosyası uygun bir FHS dizini altında oluşturulmalıdır.
- Test imaj dosyası kaynak sunucudan hedef sunucuya aktarılmalıdır.
- Aktarım sonrası checksum doğrulaması yapılmalıdır.
- Junior ve senior sistem mühendisleri kendi rollerine uygun teslimatlar üretmelidir.

---

# 8 | Junior Sistem Mühendisi Rolü

Junior sistem mühendisi, proje kapsamında uygulama, doğrulama ve dokümantasyon görevlerinden sorumludur. Bu rol, senior sistem mühendisi tarafından belirlenen standartlara göre kurulumları gerçekleştiren, komut çıktılarını doğrulayan ve yapılan işlemleri belgeleyen roldür.

Junior sistem mühendisi karar verici değil, uygulayıcı ve doğrulayıcı roldedir. Bu nedenle dağıtım seçimi, partition standardı veya production uygunluğu gibi kararları tek başına belirlemez. Ancak bu kararların uygulanabilirliğini test ortamında doğrular.

---

## 8.1 | Sanal Makine Ortamını Hazırlama

Junior sistem mühendisi, belirlenen lab topolojisine uygun olarak sanal makine ortamını hazırlar.

**Görevler:**

- Rocky Linux ve Debian için gerekli sanal makineleri oluşturunuz.
- VM kaynaklarını belirlenen CPU, RAM ve disk değerlerine göre yapılandırınız.
- Sanal makineleri şirketin naming convention standardına uygun şekilde isimlendiriniz.
- VM network yapılandırmasını test ortamına uygun şekilde hazırlayınız.
- Kurulum öncesi VM donanım kaynaklarını dokümante ediniz.

**Beklenen çıktı:**

```text
lab-topology.md
```

---

## 8.2 | ISO Dosyalarını Temin Etme ve Doğrulama

Junior sistem mühendisi, senior tarafından belirlenen Linux dağıtımlarına ait ISO dosyalarını indirir ve doğrular.

**Görevler:**

- Rocky Linux ISO dosyasını indiriniz.
- Debian ISO dosyasını indiriniz.
- ISO dosyalarının SHA256 checksum değerlerini doğrulayınız.
- Resmi checksum değeri ile lokal checksum değerini karşılaştırınız.
- Doğrulama sonuçlarını dokümante ediniz.

**Örnek komutlar:**

```bash
sha256sum Rocky-*.iso
sha256sum debian-*.iso
```

**Beklenen çıktı:**

```text
iso-validation.md
```

---

## 8.3 | Rocky Linux Minimal Sunucu Kurulumu

Rocky Linux sunucusu, Ankara lokasyonundaki kaynak sunucu olarak kullanılacaktır.

**Görevler:**

- `tr-rocky-min-01` isimli VM üzerinde Rocky Linux minimal installation kurulumu yapınız.
- Hostname değerini `tr-rocky-min-01` olarak ayarlayınız.
- Timezone değerini `Europe/Istanbul` olarak yapılandırınız.
- Keyboard layout ayarını belirlenen standarda göre seçiniz.
- Root şifresini belirleyiniz.
- Sudo yetkisine sahip standart admin kullanıcısını oluşturunuz.
- Network bağlantısını aktif hale getiriniz.
- Kurulum sonrası sisteme oturum açınız.

**Doğrulama komutları:**

```bash
hostnamectl
timedatectl
cat /etc/os-release
uname -r
ip addr
ip route
```

**Beklenen çıktı:**

```text
rocky-installation-notes.md
```

---

## 8.4 | Debian Hedef Sunucu Kurulumu

Debian sunucusu, Bakü şubesindeki hedef sunucuyu temsil edecektir.

**Görevler:**

- `az-debian-full-01` isimli VM üzerinde Debian kurulumu yapınız.
- Hostname değerini `az-debian-full-01` olarak ayarlayınız.
- Timezone değerini proje standardına göre yapılandırınız.
- Sudo yetkisine sahip standart admin kullanıcısını oluşturunuz.
- SSH servisinin kurulu ve aktif olduğunu doğrulayınız.
- Network erişimini test ediniz.
- Kurulum sonrası temel kontrolleri yapınız.

**Doğrulama komutları:**

```bash
hostnamectl
timedatectl
cat /etc/os-release
uname -r
ip addr
ip route
systemctl status ssh
```

**Beklenen çıktı:**

```text
debian-installation-notes.md
```

---

## 8.5 | Minimal ve Full Installation Karşılaştırması

Junior sistem mühendisi, kurulum profillerinin temel farklarını gözlemleyerek raporlar.

**Görevler:**

- Minimal kurulum ile full kurulum arasındaki paket farklarını inceleyiniz.
- Disk kullanımı farklarını karşılaştırınız.
- Varsayılan servis farklarını kontrol ediniz.
- GUI veya ek paketlerin sistem kaynaklarına etkisini değerlendiriniz.
- Test ortamı için kısa teknik karşılaştırma raporu hazırlayınız.

**Örnek komutlar:**

Rocky Linux:

```bash
dnf group list --installed
rpm -qa | wc -l
systemctl list-unit-files --type=service
df -h
```

Debian:

```bash
dpkg -l | wc -l
systemctl list-unit-files --type=service
df -h
```

**Beklenen çıktı:**

```text
minimal-vs-full-comparison.md
```

---

## 8.6 | Disk ve Partition Yapısını Doğrulama

Junior sistem mühendisi, kurulum sonrası disk yapısının senior tarafından belirlenen plana uygun olup olmadığını kontrol eder.

**Görevler:**

- Root filesystem kapasitesini kontrol ediniz.
- `/boot`, `/var`, `/home`, `swap` ve varsa `/srv` veya `/data` yapılarını inceleyiniz.
- Hedef sunucuda imaj dosyası için yeterli alan olduğunu doğrulayınız.
- Disk çıktılarınızı dokümante ediniz.

**Komutlar:**

```bash
lsblk
df -h
blkid
mount
findmnt
swapon --show
free -h
```

**Beklenen çıktı:**

```text
disk-validation.md
```

---

## 8.7 | FHS Yapısını İnceleme

Junior sistem mühendisi, Linux FHS yapısını proje bağlamında inceler.

**Aşağıdaki dizinlerin işlevlerini açıklayınız:**

```text
/etc
/var
/home
/boot
/usr
/tmp
/opt
/srv
```

Ayrıca aşağıdaki soruları cevaplayınız:

- Test imaj dosyası neden `/tmp` altında tutulmamalıdır?
- Test imaj dosyası neden `/root` altında tutulmamalıdır?
- `/opt/images` ve `/srv/images` kullanımının farkı nedir?
- Büyük dosyalar için ayrı bir `/data` mount point kullanmak hangi durumlarda mantıklıdır?

**Komutlar:**

```bash
ls /
ls -ld /etc /var /home /boot /usr /tmp /opt /srv
du -sh /var
df -h
```

**Beklenen çıktı:**

```text
fhs-analysis.md
```

---

## 8.8 | Test İmaj Dosyasını Oluşturma

Junior sistem mühendisi, gerçek confidential imaj yerine kullanılacak 10 MB boyutunda test imaj dosyasını oluşturur.

**Kaynak sunucuda dizin hazırlığı:**

```bash
sudo mkdir -p /opt/images
sudo chown adminuser:adminuser /opt/images
sudo chmod 750 /opt/images
```

**10 MB test dosyası oluşturma:**

```bash
cd /opt/images
dd if=/dev/zero of=boot2root-test-image.img bs=1M count=10 status=progress
```

**Kontrol:**

```bash
ls -lh /opt/images/boot2root-test-image.img
```

**Beklenen çıktı:**

```text
image-creation.md
```

---

## 8.9 | SSH Erişimini Doğrulama

Junior sistem mühendisi, kaynak ve hedef sunucu arasında SSH erişimini test eder.

**Görevler:**

- Rocky sunucudan Debian sunucuya ping testi yapınız.
- Rocky sunucudan Debian sunucuya SSH bağlantısını test ediniz.
- Hedef sunucuda SSH servisinin durumunu kontrol ediniz.
- Bağlantı başarısız olursa temel network ve servis kontrollerini yapınız.

**Komutlar:**

```bash
ping 192.168.20.10
ssh adminuser@192.168.20.10
```

Hedef Debian üzerinde:

```bash
systemctl status ssh
ss -tulpen | grep :22
```

```bash
sudo apt update
sudo apt install openssh-server -y
sudo systemctl start ssh
sudo systemctl enable ssh

sudo systemctl enable --now ssh
# İkisini tek komutla yapmak istersen

systemctl status ssh
```

**Beklenen çıktı:**

```text
ssh-connectivity-validation.md
```

---

## 8.10 | SHA256 Checksum Üretme

Junior sistem mühendisi, aktarım öncesi kaynak dosya için SHA256 checksum değeri üretir.

**Komutlar:**

```bash
cd /opt/images
sha256sum boot2root-test-image.img > boot2root-test-image.img.sha256
cat boot2root-test-image.img.sha256
```

**Beklenen çıktı:**

```text
image-checksum-source.md
```

---

## 8.11 | dd + SSH ile Dosya Aktarımı

Junior sistem mühendisi, test imaj dosyasını kaynak sunucudan hedef sunucuya `dd + ssh` yöntemiyle aktarır.

**Hedef sunucuda dizin hazırlığı:**

```bash
sudo mkdir -p /srv/images
sudo chown adminuser:adminuser /srv/images
sudo chmod 750 /srv/images
```

**Hedef disk alanı kontrolü:**

```bash
ssh adminuser@192.168.20.10 "df -h /srv/images && ls -ld /srv/images"
```

**Dosya aktarımı:**

```bash
cd /opt/images

dd if=boot2root-test-image.img bs=1M status=progress | ssh adminuser@192.168.20.10 "dd of=/srv/images/boot2root-test-image.img bs=1M status=progress"
```

**Checksum dosyasını aktarma:**

```bash
scp boot2root-test-image.img.sha256 adminuser@192.168.20.10:/srv/images/
```

**Beklenen çıktı:**

```text
image-transfer-procedure.md
```

---

## 8.12 | Hedef Sunucuda Checksum Doğrulaması

Junior sistem mühendisi, hedef sunucuda dosya bütünlüğünü doğrular.

**Komutlar:**

```bash
ssh adminuser@192.168.20.10

cd /srv/images
ls -lh
sha256sum -c boot2root-test-image.img.sha256
```

**Beklenen başarılı çıktı:**

```text
boot2root-test-image.img: OK
```

**Beklenen çıktı dosyası:**

```text
image-transfer-validation.md
```

---

## 8.13 | Post-Installation Temel Kontrolleri

Junior sistem mühendisi, her iki sunucuda temel sağlık kontrollerini çalıştırır.

**Ortak kontroller:**

```bash
hostnamectl
timedatectl
cat /etc/os-release
uname -r
ip addr
ip route
df -h
lsblk
free -h
systemctl --failed
journalctl -p err -b
```

**Rocky Linux özel kontroller:**

```bash
dnf repolist
sudo firewall-cmd --list-all
getenforce
sestatus
```

**Debian özel kontroller:**

```bash
apt update
systemctl status ssh
```

**Beklenen çıktı:**

```text
post-installation-checklist.md
```

---

# 9 | Senior Sistem Mühendisi Rolü

Senior sistem mühendisi; karar, standart, güvenlik, teknik değerlendirme ve production readiness yaklaşımından sorumludur.

Senior rolü şirketin Linux altyapısı için hangi standardın uygulanacağını belirler, junior tarafından üretilen çıktıları değerlendirir ve test ortamından production ortamına geçiş için teknik riskleri analiz eder.

---

## 9.1 | Linux Dağıtımı Seçim Analizi

Senior sistem mühendisi, proje için kullanılacak dağıtımları enterprise kriterlere göre değerlendirir.

**Değerlendirilecek dağıtımlar:**

```text
RHEL
Rocky Linux
AlmaLinux
Debian
Ubuntu Server
```

**Değerlendirme kriterleri:**

```text
- Yaşam döngüsü
- Paket yönetimi
- Enterprise destek modeli
- Güvenlik güncellemeleri
- Topluluk desteği
- RHEL ekosistemiyle uyumluluk
- Dokümantasyon kalitesi
- Operasyonel yaygınlık
```

**Beklenen çıktı:**

```text
distribution-selection.md
```

---

## 9.2 | Minimal ve Full Installation Kararı

Senior sistem mühendisi, minimal ve full installation profillerini teknik açıdan değerlendirir.

**Değerlendirme başlıkları:**

```text
- Kurulum kapsamı
- Disk kullanımı
- Paket sayısı
- Servis sayısı
- Saldırı yüzeyi
- Yönetim kolaylığı
- Production uygunluğu
```

**Beklenen değerlendirme:**

Production benzeri sunucular için varsayılan yaklaşımın minimal installation olması beklenir. Full installation profili ise eğitim, karşılaştırma veya belirli kullanım senaryoları için değerlendirilebilir.

**Beklenen çıktı:**

```text
installation-profile-decision.md
```

---

## 9.3 | Disk Partition Stratejisi

Senior sistem mühendisi, kaynak ve hedef sunucular için önerilen disk yapısını belirler.

**Değerlendirilecek mount point’ler:**

```text
/
/boot
/var
/home
swap
/opt/images
/srv/images
/data
```

**Değerlendirme noktaları:**

- Root filesystem gereğinden fazla büyümeli mi?
- `/var` ayrı partition olmalı mı?
- Log büyümesi root filesystem’i etkiler mi?
- Büyük image dosyaları `/srv/images` altında mı tutulmalı?
- Production ortamında ayrı `/data` mount point daha uygun olur mu?
- Swap alanı bu lab ortamı için gerekli mi?

**Beklenen çıktı:**

```text
partition-strategy.md
```

---

## 9.4 | Naming Convention ve IP Planı

Senior sistem mühendisi, sunucuların isimlendirme ve IP planını belirler.

**Örnek naming convention:**

```text
<lokasyon>-<dağıtım>-<profil>-<numara>
```

**Örnek hostname’ler:**

```text
tr-rocky-min-01
az-debian-full-01
```

**Beklenen çıktı:**

```text
naming-and-ip-plan.md
```

---

## 9.5 | Post-Installation Checklist Hazırlama

Senior sistem mühendisi, junior tarafından yapılan kurulumların kontrol edileceği checklist’i hazırlar.

**Checklist aşağıdaki kategorileri içermelidir:**

**Kimlik ve Standart Kontrolleri**

- Kurulan dağıtım doğru mu?
- Hostname şirket standardına uygun mu?
- Timezone doğru mu?
- Keyboard layout doğru mu?

**Kullanıcı ve Yetki Kontrolleri**

- Root şifresi şirket password politikasıyla uyumlu mu?
- Standart admin kullanıcı oluşturuldu mu?
- Kullanıcı sudo yetkisine sahip mi?

**Network ve Erişim Kontrolleri**

- Sunucular doğru IP bloklarında mı?
- Sunucular birbirine erişebiliyor mu?
- SSH servisi aktif mi?
- Firewall SSH erişimini engelliyor mu?

**Disk ve Dosya Sistemi Kontrolleri**

- Disk partition yapısı plana uygun mu?
- `/opt/images` ve `/srv/images` dizinleri doğru oluşturuldu mu?
- Hedef sunucuda yeterli disk alanı var mı?

**Paket ve Servis Kontrolleri**

- Gereksiz GUI veya paket kurulmuş mu?
- Paket yöneticisi çalışıyor mu?
- Başarısız systemd servisi var mı?

**Log Kontrolleri**

- `systemctl --failed` çıktısı temiz mi?
- `journalctl -p err -b` çıktısında kritik hata var mı?

**Beklenen çıktı:**

```text
senior-post-installation-checklist.md
```

---

## 9.6 | Junior Çıktılarını Review Etme

Senior sistem mühendisi, junior tarafından hazırlanan çıktıları inceler.

**Review edilecek dosyalar:**

```text
iso-validation.md
rocky-installation-notes.md
debian-installation-notes.md
minimal-vs-full-comparison.md
disk-validation.md
fhs-analysis.md
image-transfer-validation.md
post-installation-checklist.md
```

**Review sırasında cevaplanması gereken sorular:**

- Kurulumlar belirlenen standarda uygun mu?
- Hostname ve IP planı doğru uygulanmış mı?
- ISO doğrulaması yapılmış mı?
- Disk yapısı beklenen plana uygun mu?
- Image dosyası doğru dizinde mi tutuluyor?
- Checksum doğrulaması başarılı mı?
- Loglarda kritik hata var mı?
- Dokümantasyon yeterli mi?

**Beklenen çıktı:**

```text
senior-review-report.md
```

---

## 9.7 | Dosya Aktarım Prosedürünü Değerlendirme

Senior sistem mühendisi, test ortamında yapılan `dd + ssh` aktarım sürecini değerlendirir.

**Değerlendirme başlıkları:**

```text
- dd + ssh yönteminin avantajları
- dd + ssh yönteminin riskleri
- Checksum doğrulamasının zorunlu olması
- Aktarım öncesi disk alanı kontrolü
- Aktarım sonrası dosya boyutu kontrolü
- Aktarım sonrası SHA256 doğrulaması
- Production ortamında daha güvenli ve verimli yöntem önerileri
```

**Beklenen çıktı:**

```text
image-transfer-standard.md
```

---

## 9.8 | Production Readiness Değerlendirmesi

Senior sistem mühendisi, test ortamı sonuçlarına göre production geçişi için değerlendirme yapar.

**Değerlendirilecek konular:**

```text
- Kurulum standardı production için yeterli mi?
- Minimal installation profili uygun mu?
- Disk planı büyük imaj dosyaları için yeterli mi?
- Dosya aktarım prosedürü güvenli mi?
- Checksum doğrulaması zorunlu hale getirildi mi?
- Log ve servis kontrolleri yeterli mi?
- Otomasyon ihtiyacı var mı?
- Monitoring ve backup ihtiyacı var mı?
```

**Beklenen çıktı:**

```text
production-readiness-report.md
```

---

# 10 | Olası Hata Alanları ve Troubleshooting Başlıkları

Bu projede aşağıdaki hata alanlarına karşı hazırlıklı olmanız beklenir. Bu bölüm, sadece başarılı kurulum yapmasını değil, aynı zamanda hata belirtilerini analiz edebilmesii amaçlar.

---

## 10.1 | Yanlış Hostname

**Belirti:**

Sunucu adı şirket standardına uygun değildir.

**Kontrol komutları:**

```bash
hostnamectl
cat /etc/hostname
```

**Beklenen yaklaşım:**

Hostname standardı kontrol edilmeli, yanlış isimlendirme varsa düzeltilmeli ve dokümante edilmelidir.

---

## 10.2 | Yanlış Timezone

**Belirti:**

Sistem zamanı veya log zamanları beklenen lokasyonla uyuşmaz.

**Kontrol komutları:**

```bash
timedatectl
date
```

**Beklenen yaklaşım:**

Timezone ayarı kontrol edilmeli ve proje standardına uygun hale getirilmelidir.

---

## 10.3 | SSH Servisi Çalışmıyor

**Belirti:**

Hedef sunucuya SSH bağlantısı kurulamaz.

**Kontrol komutları:**

```bash
systemctl status ssh
systemctl status sshd
ss -tulpen | grep :22
```

**Beklenen yaklaşım:**

Dağıtıma göre servis adı kontrol edilmeli, SSH servisinin aktif ve erişilebilir olduğu doğrulanmalıdır.

---

## 10.4 | Firewall SSH Erişimini Engelliyor

**Belirti:**

SSH servisi çalışıyor görünür, ancak dışarıdan bağlantı kurulamaz.

**Kontrol komutları:**

```bash
sudo firewall-cmd --list-all
```

**Beklenen yaklaşım:**

Servis çalışıyor olsa bile firewall katmanının bağlantıyı engelleyip engellemediği kontrol edilmelidir.

---

## 10.5 | Hedef Dizin Yetki Hatası

**Belirti:**

`dd` komutu hedef dosyayı yazamaz.

**Örnek hata:**

```text
dd: failed to open '/srv/images/boot2root-test-image.img': Permission denied
```

**Kontrol komutları:**

```bash
ls -ld /srv/images
id
```

**Beklenen yaklaşım:**

Dizin sahipliği ve izinleri kontrol edilmeli, ilgili kullanıcının yazma yetkisi doğrulanmalıdır.

---

## 10.6 | Hedef Diskte Yeterli Alan Yok

**Belirti:**

Aktarım yarıda kesilir veya hedef sistem dosyayı tam yazamaz.

**Örnek hata:**

```text
No space left on device
```

**Kontrol komutları:**

```bash
df -h /srv/images
lsblk
```

**Beklenen yaklaşım:**

Aktarım öncesinde hedef dizinin bağlı olduğu dosya sisteminde yeterli boş alan olduğu doğrulanmalıdır.

---

## 10.7 | Checksum Doğrulaması Başarısız

**Belirti:**

```text
boot2root-test-image.img: FAILED
sha256sum: WARNING: 1 computed checksum did NOT match
```

**Olası nedenler:**

- Dosya eksik aktarılmıştır.
- Yanlış dosya aktarılmıştır.
- Checksum dosyası eski sürüme aittir.
- Kaynak dosya checksum üretildikten sonra değişmiştir.
- Aktarım sırasında bağlantı kopmuştur.

**Kontrol komutları:**

```bash
ls -lh
sha256sum boot2root-test-image.img
cat boot2root-test-image.img.sha256
```

**Beklenen yaklaşım:**

Checksum uyuşmazlığı giderilmeden dosya test sürecine alınmamalıdır.

---

## 10.8 | Checksum Dosyası Yanlış Path İçeriyor

**Belirti:**

```text
sha256sum: /opt/images/boot2root-test-image.img: No such file or directory
```

**Beklenen yaklaşım:**

Checksum dosyası mümkün olduğunca relative path ile üretilmelidir.

Örnek:

```bash
cd /opt/images
sha256sum boot2root-test-image.img > boot2root-test-image.img.sha256
```

---

# 11 | Proje Kabul Kriterleri

Projenin başarılı sayılması için aşağıdaki kriterler karşılanmalıdır:

- Rocky Linux ve Debian sunucuları başarıyla kurulmuş olmalıdır.
- ISO dosyalarının SHA256 doğrulaması yapılmış olmalıdır.
- Minimal ve full installation farkları raporlanmış olmalıdır.
- Hostname, timezone, keyboard layout ve kullanıcı yapılandırmaları tamamlanmış olmalıdır.
- Disk partition yapısı doğrulanmış olmalıdır.
- FHS dizinleri proje bağlamında açıklanmış olmalıdır.
- Kaynak sunucuda 10 MB test imaj dosyası oluşturulmuş olmalıdır.
- Test imaj dosyası `dd + ssh` yöntemiyle hedef sunucuya aktarılmış olmalıdır.
- Hedef sunucuda `sha256sum -c` sonucu `OK` dönmelidir.
- SSH, network, servis ve log kontrolleri tamamlanmış olmalıdır.
- Junior görev çıktıları dokümante edilmiş olmalıdır.
- Senior review raporu hazırlanmış olmalıdır.
- Production readiness değerlendirmesi tamamlanmış olmalıdır.

---

# 12 | Teslim Edilecek Dokümanlar

Proje sonunda aşağıdaki dosyalar hazırlanmalıdır:

```text
README.md
project-scenario.md
lab-topology.md
naming-and-ip-plan.md
iso-validation.md
distribution-selection.md
installation-profile-decision.md
minimal-vs-full-comparison.md
partition-strategy.md
rocky-installation-notes.md
debian-installation-notes.md
disk-validation.md
fhs-analysis.md
image-creation.md
image-transfer-procedure.md
image-transfer-validation.md
post-installation-checklist.md
senior-post-installation-checklist.md
senior-review-report.md
image-transfer-standard.md
troubleshooting.md
production-readiness-report.md
commands-used.md
```

---

# 13 | Önerilen Dizin Yapısı

```text
Project-01-Boot2Root-Linux-Deployment/
├── README.md
├── docs/
│   ├── project-scenario.md
│   ├── lab-topology.md
│   ├── naming-and-ip-plan.md
│   ├── iso-validation.md
│   ├── distribution-selection.md
│   ├── installation-profile-decision.md
│   ├── minimal-vs-full-comparison.md
│   ├── partition-strategy.md
│   ├── rocky-installation-notes.md
│   ├── debian-installation-notes.md
│   ├── disk-validation.md
│   ├── fhs-analysis.md
│   ├── image-creation.md
│   ├── image-transfer-procedure.md
│   ├── image-transfer-validation.md
│   ├── post-installation-checklist.md
│   ├── senior-post-installation-checklist.md
│   ├── senior-review-report.md
│   ├── image-transfer-standard.md
│   ├── troubleshooting.md
│   └── production-readiness-report.md
├── commands/
│   └── commands-used.md
├── screenshots/
│   ├── rocky-installation/
│   ├── debian-installation/
│   ├── disk-layout/
│   ├── ssh-tests/
│   ├── checksum-validation/
│   └── troubleshooting/
└── configs/
    ├── sample-hostname.txt
    ├── sample-ip-plan.txt
    └── sample-checksum-output.txt
```

---

# 14 | Post-Installation Checklist Uygulaması

## 14.1 | Kimlik ve Standart Kontrolleri

---

### 14.1.1 | Kurulan dağıtım doğru mu?

#### Amaç

Sunucuya gerçekten beklenen Linux dağıtımının kurulup kurulmadığını doğrulamak.

#### Komutlar

```bash
cat /etc/os-release
hostnamectl
uname -r
```

#### Rocky Linux beklenen örnek çıktı

```text
NAME="Rocky Linux"
VERSION="9.x"
ID="rocky"
```

#### Debian beklenen örnek çıktı

```text
PRETTY_NAME="Debian GNU/Linux 13 (trixie)"
ID=debian
```

#### Olası hata

Yanlış ISO ile kurulum yapılmış olabilir. Örneğin Rocky beklenirken AlmaLinux, Debian beklenirken Ubuntu kurulmuş olabilir.

#### Kontrol yaklaşımı

```bash
cat /etc/os-release
```

Buradaki `ID`, `NAME` ve `VERSION_ID` alanları kontrol edilir.

#### Düzeltme

Yanlış dağıtım kurulmuşsa production standardı açısından en doğru çözüm genellikle yeniden kurulumdur.

```text
Aksiyon:
Yanlış kurulan VM silinir veya arşivlenir.
Doğru ISO ile kurulum yeniden yapılır.
```

---

### 14.1.2 | Hostname şirket standardına uygun mu?

#### Amaç

Sunucu adının şirket naming convention standardına uyup uymadığını kontrol etmek.

Örnek standart:

```text
<lokasyon>-<dağıtım>-<profil>-<numara>
```

Örnek hostname’ler:

```text
tr-rocky-min-01
az-debian-full-01
```

#### Komutlar

```bash
hostnamectl
hostname
cat /etc/hostname
```

#### Beklenen çıktı

```text
Static hostname: tr-rocky-min-01
```

veya:

```text
Static hostname: az-debian-full-01
```

#### Olası hata

Hostname şu şekilde kalmış olabilir:

```text
localhost
server
linux
debian
rocky
```

#### Düzeltme

Rocky veya Debian üzerinde:

```bash
sudo hostnamectl set-hostname tr-rocky-min-01
```

Debian hedef sunucu için:

```bash
sudo hostnamectl set-hostname az-debian-full-01
```

#### Doğrulama

```bash
hostnamectl
```

#### Not

Hostname yalnızca ekranda görünen isim değildir. Inventory, log yönetimi, monitoring, SSH erişimi ve otomasyon süreçlerinde sistem kimliği olarak kullanılır.

---

### 14.1.3 | Timezone doğru mu?

#### Amaç

Sunucu zamanının ve log kayıtlarının doğru zaman dilimine göre tutulduğunu kontrol etmek.

#### Komutlar

```bash
timedatectl
date
```

#### Beklenen çıktı

Türkiye lokasyonu için:

```text
Time zone: Europe/Istanbul
```

Azerbaycan lokasyonu için tercih edilirse:

```text
Time zone: Asia/Baku
```

#### Olası hata

Timezone şu şekilde kalmış olabilir:

```text
UTC
America/New_York
Europe/London
```

Bu durumda log analizlerinde zaman karışıklığı oluşabilir.

#### Düzeltme

Türkiye için:

```bash
sudo timedatectl set-timezone Europe/Istanbul
```

Azerbaycan için:

```bash
sudo timedatectl set-timezone Asia/Baku
```

#### Doğrulama

```bash
timedatectl
date
```

---

### 14.1.4 | Keyboard layout doğru mu?

#### Amaç

Klavye düzeninin doğru olup olmadığını kontrol etmek. Özellikle özel karakter içeren parolalarda ve komutlarda önemlidir.

#### Komutlar

```bash
localectl
```

#### Beklenen çıktı örneği

```text
VC Keymap: trq
X11 Layout: tr
```

veya İngilizce klavye tercih edildiyse:

```text
VC Keymap: us
X11 Layout: us
```

#### Olası hata

Klavye düzeni yanlış seçildiyse şu karakterlerde sorun yaşanabilir:

```text
@
/
\
-
_
:
"
```

#### Düzeltme

Türkçe Q klavye için:

```bash
sudo localectl set-keymap trq
```

İngilizce klavye için:

```bash
sudo localectl set-keymap us
```

#### Doğrulama

```bash
localectl
```

---

## 14.2 | Kullanıcı ve Yetki Kontrolleri

---

### 14.2.1 | Root şifresi şirket password politikasıyla uyumlu mu?

#### Amaç

Root hesabının güvenli parola politikasına uygun yapılandırıldığını doğrulamak.

#### Kontrol

Linux sistemlerde mevcut root parolası düz metin olarak görüntülenemez. Bu nedenle kontrol, parola değerini görmek üzerinden değil; hesabın durumu, parola yaşlandırma politikası ve erişim yaklaşımı üzerinden yapılır.

#### Komutlar

```bash
sudo passwd -S root
sudo chage -l root
```

#### Beklenen yorum

```text
root hesabı aktif mi?
Parola belirlenmiş mi?
Parola yaşlandırma politikası var mı?
Root doğrudan SSH ile erişebilir mi?
```

#### Root SSH kontrolü

Rocky ve Debian’da SSH yapılandırması:

```bash
sudo grep -i "^PermitRootLogin" /etc/ssh/sshd_config
```

Eğer satır yoksa tüm ilgili ayarları görmek için:

```bash
sudo sshd -T | grep permitrootlogin
```

#### Olası riskli çıktı

```text
permitrootlogin yes
```

#### Daha güvenli yaklaşım

```text
permitrootlogin no
```

veya bazı sistemlerde:

```text
permitrootlogin prohibit-password
```

#### Düzeltme

SSH config dosyasını aç:

```bash
sudo nano /etc/ssh/sshd_config
```

Şu ayarı kullanın:

```text
PermitRootLogin no
```

Servisi yeniden başlatın:

Debian:

```bash
sudo systemctl restart ssh
```

Rocky:

```bash
sudo systemctl restart sshd
```

---

### 14.2.2 | Standart admin kullanıcı oluşturuldu mu?

#### Amaç

Günlük yönetim işlemlerinin doğrudan root hesabı yerine standart bir admin kullanıcıyla yapılmasını sağlamak.

Örnek kullanıcı:

```text
adminuser
```

#### Komutlar

```bash
id adminuser
getent passwd adminuser
```

#### Beklenen çıktı

```text
uid=1000(adminuser) gid=1000(adminuser) groups=1000(adminuser),...
```

#### Olası hata

```text
id: ‘adminuser’: no such user
```

#### Düzeltme

Rocky/Debian ortak:

```bash
sudo useradd -m adminuser
sudo passwd adminuser
```

Debian’da bazı sistemlerde `useradd` yerine `adduser` daha kullanıcı dostudur:

```bash
sudo adduser adminuser
```

### Doğrulama

```bash
id adminuser
getent passwd adminuser
```

---

### 14.2.3 | Kullanıcı sudo yetkisine sahip mi?

#### Amaç

Admin kullanıcının yönetimsel komutları `sudo` ile çalıştırabildiğini doğrulamak.

#### Rocky Linux kontrolü

Rocky’de genellikle `wheel` grubu kullanılır.

```bash
groups adminuser
id adminuser
```

Beklenen:

```text
wheel
```

Sudo testi:

```bash
sudo -l
```

veya:

```bash
sudo whoami
```

Beklenen çıktı:

```text
root
```

#### Debian kontrolü

Debian’da genellikle `sudo` grubu kullanılır.

```bash
groups adminuser
id adminuser
```

Beklenen:

```text
sudo
```

Sudo testi:

```bash
sudo whoami
```

Beklenen çıktı:

```text
root
```

#### Olası hata

```text
adminuser is not in the sudoers file.
```

veya:

```text
adminuser is not allowed to run sudo
```

#### Rocky düzeltme

```bash
sudo usermod -aG wheel adminuser
```

#### Debian düzeltme

```bash
sudo usermod -aG sudo adminuser
```

#### Önemli not

Grup eklemesinden sonra kullanıcının yeniden oturum açması gerekir.

#### Doğrulama

```bash
su - adminuser
groups
sudo whoami
```

---

## 14.3 | Network ve Erişim Kontrolleri

---

### 14.3.1 | Sunucular doğru IP bloklarında mı?

#### Amaç

Sunucuların proje IP planına uygun yapılandırıldığını kontrol etmek.

Örnek IP planı:

```text
tr-rocky-min-01     192.168.10.10
az-debian-full-01   192.168.20.10
```

#### Komutlar

```bash
ip addr
ip route
hostname -I
```

Daha sade çıktı için:

```bash
ip -br addr
```

#### Beklenen çıktı

Rocky:

```text
192.168.10.10
```

Debian:

```text
192.168.20.10
```

#### Olası hatalar

```text
IP adresi alınmamış olabilir.
Yanlış network bloğundan IP alınmış olabilir.
Interface down durumda olabilir.
Default gateway eksik olabilir.
```

#### Network interface durumu

```bash
nmcli device status
```

#### Rocky/Debian NetworkManager kullanıyorsa IP kontrolü

```bash
nmcli connection show
```

#### Interface aktif değilse

Bağlantı adını öğren:

```bash
nmcli connection show
```

Bağlantıyı aç:

```bash
sudo nmcli connection up "CONNECTION_NAME"
```

Autoconnect aktif et:

```bash
sudo nmcli connection modify "CONNECTION_NAME" connection.autoconnect yes
```

#### Doğrulama

```bash
ip -br addr
ip route
```

---

### 14.3.2 | Sunucular birbirine erişebiliyor mu?

#### Amaç

Kaynak ve hedef sunucu arasında temel network erişimini doğrulamak.

#### Komutlar

Rocky’den Debian’a:

```bash
ping -c 4 192.168.20.10
```

Debian’dan Rocky’ye:

```bash
ping -c 4 192.168.10.10
```

Route kontrolü:

```bash
ip route
```

#### Port bazlı bağlantı testi

Ping başarılı olsa bile SSH çalışmayabilir. SSH portunu ayrıca test etmek gerekir.

```bash
nc -vz 192.168.20.10 22
```

`nc` yoksa:

```bash
ssh -v adminuser@192.168.20.10
```

#### Olası hata

```text
Destination Host Unreachable
```

veya:

```text
Request timed out
```

#### Muhtemel nedenler

```text
Yanlış IP adresi
Yanlış network adapter
Gateway eksik
Firewall engeli
Hedef sunucu kapalı
Interface down
```

#### Kontrol komutları

```bash
ip addr
ip route
nmcli device status
ping -c 4 <gateway-ip>
```

---

### 14.3.3 | SSH servisi aktif mi?

#### Amaç

Sunucuya uzaktan erişim için SSH servisinin çalıştığını doğrulamak.

#### Debian

Servis adı genellikle:

```text
ssh
```

Kontrol:

```bash
systemctl status ssh
systemctl is-enabled ssh
ss -tulpen | grep :22
```

Başlatma:

```bash
sudo systemctl enable --now ssh
```

#### Rocky Linux

Servis adı genellikle:

```text
sshd
```

Kontrol:

```bash
systemctl status sshd
systemctl is-enabled sshd
ss -tulpen | grep :22
```

Başlatma:

```bash
sudo systemctl enable --now sshd
```

#### Olası hata

```text
Unit ssh.service could not be found.
```

Rocky’de `ssh` yerine `sshd` kullanılması gerekir.

```bash
systemctl status sshd
```

Debian’da SSH kurulu değilse:

```bash
sudo apt update
sudo apt install -y openssh-server
sudo systemctl enable --now ssh
```

Rocky’de SSH kurulu değilse:

```bash
sudo dnf install -y openssh-server
sudo systemctl enable --now sshd
```

#### Doğrulama

```bash
ss -tulpen | grep :22
```

Beklenen:

```text
LISTEN ... :22
```

---

### 14.3.4 | Firewall SSH erişimini engelliyor mu?

#### Amaç

SSH servisi çalışsa bile firewall bağlantıyı engelleyebilir. Bu katmanın ayrıca kontrol edilmesi gerekir.

#### Rocky Linux firewalld kontrolü

```bash
sudo firewall-cmd --state
sudo firewall-cmd --list-all
```

SSH açık mı?

```bash
sudo firewall-cmd --list-services
```

Beklenen servis:

```text
ssh
```

#### SSH izni ekleme

```bash
sudo firewall-cmd --permanent --add-service=ssh
sudo firewall-cmd --reload
```

#### Doğrulama

```bash
sudo firewall-cmd --list-all
```

#### Debian UFW kullanılıyorsa

UFW kurulu olmayabilir. Kontrol:

```bash
sudo ufw status
```

Eğer `ufw: command not found` dönerse, sistem UFW kullanmıyor olabilir.

UFW aktifse SSH izni:

```bash
sudo ufw allow ssh
sudo ufw status
```

#### nftables kontrolü

Debian veya modern sistemlerde nftables kullanılabilir:

```bash
sudo nft list ruleset
```

#### Olası hata

```text
Connection timed out
```

Muhtemel neden firewall veya routing olabilir.

```text
Connection refused
```

Muhtemel neden SSH servisinin çalışmaması olabilir.

---

## 14.4 | Disk ve Dosya Sistemi Kontrolleri

---

### 14.4.1 | Disk partition yapısı plana uygun mu?

#### Amaç

Kurulum sırasında belirlenen disk partition stratejisinin uygulanıp uygulanmadığını kontrol etmek.

#### Komutlar

```bash
lsblk
lsblk -f
df -h
findmnt
blkid
swapon --show
```

#### Beklenen kontrol başlıkları

```text
/ hangi partition üzerinde?
/boot ayrı mı?
/var ayrı mı?
swap var mı?
/srv veya /data ayrı mı?
Disk boyutu plana uygun mu?
```

#### Örnek çıktı

```text
sda
├─sda1  /boot
├─sda2  /
├─sda3  /var
└─sda4  [SWAP]
```

#### Olası hata

`/var` ayrı partition olarak planlanmıştır ama görünmüyordur.

Kontrol:

```bash
findmnt /var
df -h /var
```

Eğer `/var`, `/` altında görünüyorsa ayrı partition yapılmamıştır.

#### Düzeltme

Bu seviyede en temiz çözüm genellikle yeniden kurulum veya ileri derslerde LVM/mount yönetimiyle düzeltmedir.

```text
Aksiyon:
Disk planı senior review raporuna hata olarak yazılır.
Production standardına uygun yeniden kurulum önerilir.
```

---

### 14.4.2 | `/opt/images` ve `/srv/images` dizinleri doğru oluşturuldu mu?

#### Amaç

Test imaj dosyasının FHS mantığına uygun ve kontrollü bir dizinde tutulduğunu doğrulamak.

#### Kaynak Rocky sunucuda beklenen dizin

```text
/opt/images
```

#### Hedef Debian sunucuda beklenen dizin

```text
/srv/images
```

#### Kontrol komutları

```bash
ls -ld /opt/images
ls -ld /srv/images
```

#### Kaynak sunucuda dizin oluşturma

```bash
sudo mkdir -p /opt/images
sudo chown adminuser:adminuser /opt/images
sudo chmod 750 /opt/images
```

#### Hedef sunucuda dizin oluşturma

```bash
sudo mkdir -p /srv/images
sudo chown adminuser:adminuser /srv/images
sudo chmod 750 /srv/images
```

#### Doğrulama

```bash
ls -ld /opt/images
ls -ld /srv/images
```

Beklenen örnek:

```text
drwxr-x--- adminuser adminuser /srv/images
```

#### Olası hata

```text
Permission denied
```

#### Kontrol

```bash
id adminuser
ls -ld /srv/images
namei -l /srv/images
```

#### Düzeltme

```bash
sudo chown adminuser:adminuser /srv/images
sudo chmod 750 /srv/images
```

---

### 14.4.3 | Hedef sunucuda yeterli disk alanı var mı?

#### Amaç

Dosya aktarımı öncesi hedefte yeterli alan olup olmadığını doğrulamak.

#### Komutlar

```bash
df -h /srv/images
du -sh /srv/images
lsblk
```

#### Test imaj dosyası için kaynakta boyut kontrolü

```bash
ls -lh /opt/images/boot2root-test-image.img
du -h /opt/images/boot2root-test-image.img
```

#### Hedefte boş alan kontrolü

```bash
ssh adminuser@192.168.20.10 "df -h /srv/images"
```

#### Olası hata

Aktarım sırasında:

```text
No space left on device
```

#### Düzeltme seçenekleri

```text
Gereksiz test dosyalarını sil.
Hedef dizini daha büyük bir mount point altına taşı.
Disk kapasitesini artır.
Ayrı /data veya /srv mount point planla.
```

#### Güvenli temizlik örneği

```bash
sudo rm -f /srv/images/boot2root-test-image.img
```

Dikkat: `rm` komutunda dosya yolu doğru yazılmalıdır.

---

## 14.5 | Paket ve Servis Kontrolleri

---

### 14.5.1 | Gereksiz GUI veya paket kurulmuş mu?

#### Amaç

Minimal kurulum beklenen sistemde gereksiz grafik arayüz, paket grubu veya servis olup olmadığını kontrol etmek.

#### Rocky Linux paket grupları

```bash
dnf group list --installed
```

Kurulu paket sayısı:

```bash
rpm -qa | wc -l
```

Varsayılan target:

```bash
systemctl get-default
```

GUI target kontrolü:

```bash
systemctl get-default
```

Sunucu için beklenen:

```text
multi-user.target
```

GUI için:

```text
graphical.target
```

#### Debian paket sayısı

```bash
dpkg -l | wc -l
```

Desktop paketleri kontrolü:

```bash
dpkg -l | grep -Ei "gnome|kde|xfce|lxde|plasma"
```

Varsayılan target:

```bash
systemctl get-default
```

#### Olası hata

Minimal kurulum beklenirken GUI kurulmuş olabilir.

Belirti:

```text
graphical.target
```

veya GNOME/KDE paketleri görünür.

#### Düzeltme

Sunucu moduna almak için:

```bash
sudo systemctl set-default multi-user.target
```

Anlık olarak CLI moda geçmek için:

```bash
sudo systemctl isolate multi-user.target
```

Paket kaldırma konusu dikkatli yapılmalıdır.

```text
Aksiyon:
Gereksiz paketler senior review raporuna yazılır.
Production için minimal kurulum önerilir.
```

---

### 5.2 | Paket yöneticisi çalışıyor mu?

#### Amaç

Sistemin paket depolarına erişebildiğini ve güncelleme/kurulum yapabilecek durumda olduğunu kontrol etmek.

#### Rocky Linux

Repo kontrolü:

```bash
dnf repolist
```

Cache oluşturma:

```bash
sudo dnf makecache
```

Güncelleme kontrolü:

```bash
sudo dnf check-update
```

Not: `dnf check-update` güncelleme varsa `100` exit code döndürebilir. Bu tek başına hata değildir.

#### Debian

Repo güncelleme:

```bash
sudo apt update
```

Paket kaynakları:

```bash
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d/
```

#### Olası hatalar

DNS hatası:

```text
Temporary failure resolving
```

Repo erişim hatası:

```text
Cannot download repomd.xml
```

Debian tarafında:

```text
Failed to fetch
```

#### Kontrol yaklaşımı

```bash
ping -c 4 8.8.8.8
ping -c 4 debian.org
cat /etc/resolv.conf
ip route
```

#### DNS düzeltme örneği

NetworkManager kullanılan sistemde:

```bash
nmcli connection show
```

Bağlantı adını öğrendikten sonra:

```bash
sudo nmcli connection modify "CONNECTION_NAME" ipv4.dns "8.8.8.8 1.1.1.1"
sudo nmcli connection down "CONNECTION_NAME"
sudo nmcli connection up "CONNECTION_NAME"
```

### Doğrulama

Rocky:

```bash
sudo dnf makecache
```

Debian:

```bash
sudo apt update
```

---

### 14.5.3 | Başarısız systemd servisi var mı?

#### Amaç

Kurulum sonrası başarısız servis olup olmadığını kontrol etmek.

#### Komutlar

```bash
systemctl --failed
```

Tüm servisleri görmek için:

```bash
systemctl list-units --type=service
```

Belirli bir servis için:

```bash
systemctl status <service-name>
```

Detaylı log için:

```bash
journalctl -u <service-name> -b
```

#### Beklenen çıktı

```text
0 loaded units listed.
```

veya:

```text
No failed units.
```

#### Olası hata

Örneğin SSH servisi başarısız olabilir:

```text
ssh.service loaded failed failed OpenBSD Secure Shell server
```

veya Rocky tarafında:

```text
sshd.service loaded failed failed OpenSSH server daemon
```

#### Kontrol

Debian:

```bash
systemctl status ssh
journalctl -u ssh -b
```

Rocky:

```bash
systemctl status sshd
journalctl -u sshd -b
```

#### Düzeltme örneği

SSH yapılandırma testi:

```bash
sudo sshd -t
```

Eğer hata yoksa yeniden başlat:

Debian:

```bash
sudo systemctl restart ssh
```

Rocky:

```bash
sudo systemctl restart sshd
```

---

## 14.6 | Log Kontrolleri

---

### 14.6.1 | `systemctl --failed` çıktısı temiz mi?

#### Amaç

Boot sonrası başarısız systemd unit olup olmadığını görmek.

#### Komut

```bash
systemctl --failed
```

#### Beklenen çıktı

```text
0 loaded units listed.
```

#### Olası hata

Başarısız servis listelenebilir.

Örnek:

```text
NetworkManager-wait-online.service loaded failed failed
```

#### İnceleme

```bash
systemctl status NetworkManager-wait-online.service
journalctl -u NetworkManager-wait-online.service -b
```

#### Yaklaşım

Her failed servis kritik olmayabilir. Ancak production öncesi tüm failed unit’ler incelenmeli ve raporlanmalıdır.

---

### 14.6.2 | `journalctl -p err -b` çıktısında kritik hata var mı?

#### Amaç

Mevcut boot sürecindeki error seviyesindeki logları kontrol etmek.

#### Komut

```bash
journalctl -p err -b
```

Daha okunabilir çıktı:

```bash
journalctl -p err -b --no-pager
```

Son 50 satır:

```bash
journalctl -p err -b --no-pager | tail -50
```

#### Beklenen durum

Kritik servis, disk, network veya authentication hatası olmamalıdır.

#### Olası hata örnekleri

```text
Failed to start OpenSSH server daemon
```

```text
Failed to mount /srv/images
```

```text
No space left on device
```

```text
Authentication failure
```

#### Servis bazlı inceleme

```bash
journalctl -u ssh -b
journalctl -u sshd -b
journalctl -u NetworkManager -b
```

#### Kernel mesajlarını kontrol

```bash
dmesg -T | tail -50
```

#### Yaklaşım

Her error mesajı aynı önemde değildir.

```text
Kritik hata mı?
Geçici uyarı mı?
Servis çalışmasını etkiliyor mu?
Disk, network veya erişim problemi üretiyor mu?
Tekrar ediyor mu?
```

---

## 14.7 | Dosya Aktarımı ve Checksum Kontrolü

Bu checklist’in proje bağlamındaki en önemli uygulama bölümlerinden biridir.

---

### 14.7.1 | Kaynak sunucuda test imaj dosyası var mı?

#### Komutlar

```bash
ls -lh /opt/images/
file /opt/images/boot2root-test-image.img
du -h /opt/images/boot2root-test-image.img
```

#### Yoksa oluştur

```bash
sudo mkdir -p /opt/images
sudo chown adminuser:adminuser /opt/images
cd /opt/images
dd if=/dev/zero of=boot2root-test-image.img bs=1M count=10 status=progress
```

---

### 14.7.2 | Checksum üretildi mi?

#### Komut

```bash
cd /opt/images
sha256sum boot2root-test-image.img > boot2root-test-image.img.sha256
cat boot2root-test-image.img.sha256
```

#### Olası hata

Checksum dosyası absolute path ile üretilirse hedefte doğrulama problem çıkarabilir.

Yanlış örnek:

```bash
sha256sum /opt/images/boot2root-test-image.img > boot2root-test-image.img.sha256
```

Hedefte `/opt/images/...` yolu yoksa doğrulama hata verebilir.

#### Doğru yaklaşım

```bash
cd /opt/images
sha256sum boot2root-test-image.img > boot2root-test-image.img.sha256
```

---

### 14.7.3 | Hedef dizin hazır mı?

#### Komut

```bash
ssh adminuser@192.168.20.10 "ls -ld /srv/images"
```

Yoksa:

```bash
ssh adminuser@192.168.20.10 "sudo mkdir -p /srv/images && sudo chown adminuser:adminuser /srv/images && sudo chmod 750 /srv/images"
```

---

### 14.7.4 | `dd + ssh` ile aktarım çalışıyor mu?

#### Komut

```bash
cd /opt/images

dd if=boot2root-test-image.img bs=1M status=progress | ssh adminuser@192.168.20.10 "dd of=/srv/images/boot2root-test-image.img bs=1M status=progress"
```

Checksum dosyasını gönder:

```bash
scp boot2root-test-image.img.sha256 adminuser@192.168.20.10:/srv/images/
```

#### Olası hata 1

```text
Permission denied
```

Kontrol:

```bash
ssh adminuser@192.168.20.10 "ls -ld /srv/images && id"
```

Düzeltme:

```bash
ssh adminuser@192.168.20.10 "sudo chown adminuser:adminuser /srv/images"
```

#### Olası hata 2

```text
No space left on device
```

Kontrol:

```bash
ssh adminuser@192.168.20.10 "df -h /srv/images"
```

#### Olası hata 3

```text
ssh: connect to host 192.168.20.10 port 22: Connection timed out
```

Kontrol:

```bash
ping -c 4 192.168.20.10
ssh -v adminuser@192.168.20.10
```

---

### 14.7.5 | Hedefte checksum doğrulaması başarılı mı?

#### Komut

```bash
ssh adminuser@192.168.20.10
cd /srv/images
sha256sum -c boot2root-test-image.img.sha256
```

#### Beklenen çıktı

```text
boot2root-test-image.img: OK
```

#### Hata

```text
boot2root-test-image.img: FAILED
```

#### İnceleme

```bash
ls -lh
sha256sum boot2root-test-image.img
cat boot2root-test-image.img.sha256
```

#### Yaklaşım

Checksum `OK` dönmeden dosya test sürecine alınmamalıdır.

---

# 15 | Checklist Komutları

## 15.1 | Genel sistem kontrolü

```bash
hostnamectl
timedatectl
localectl
cat /etc/os-release
uname -r
```

## 15.2 | Kullanıcı ve yetki kontrolü

```bash
id adminuser
groups adminuser
sudo -l
sudo whoami
sudo passwd -S root
sudo chage -l root
```

## 15.3 | Network ve SSH kontrolü

```bash
ip -br addr
ip route
ping -c 4 192.168.20.10
systemctl status ssh
systemctl status sshd
ss -tulpen | grep :22
```

## 15.4 | Disk kontrolü

```bash
lsblk
lsblk -f
df -h
findmnt
swapon --show
free -h
```

## 15.5 | Paket ve servis kontrolü

Rocky:

```bash
dnf repolist
dnf group list --installed
rpm -qa | wc -l
systemctl get-default
systemctl --failed
```

Debian:

```bash
apt update
dpkg -l | wc -l
systemctl get-default
systemctl --failed
```

## 15.6 | Log kontrolü

```bash
journalctl -p err -b --no-pager
dmesg -T | tail -50
```

---

# 16 | Uygulama Tablosu

| Kontrol Alanı    | Komut                          | Beklenen Sonuç           | Olası Hata                         |
| ---------------- | ------------------------------ | ------------------------ | ---------------------------------- |
| Dağıtım kontrolü | `cat /etc/os-release`          | Doğru dağıtım görünür    | Yanlış ISO kurulmuş                |
| Hostname         | `hostnamectl`                  | Standarta uygun hostname | `localhost`, `server`, yanlış isim |
| Timezone         | `timedatectl`                  | Doğru timezone           | UTC veya yanlış bölge              |
| Keyboard         | `localectl`                    | Doğru keymap             | Özel karakter sorunları            |
| Admin kullanıcı  | `id adminuser`                 | Kullanıcı mevcut         | Kullanıcı oluşturulmamış           |
| Sudo yetkisi     | `sudo whoami`                  | `root`                   | sudo yetkisi yok                   |
| IP kontrolü      | `ip -br addr`                  | Doğru IP bloğu           | Yanlış IP veya interface down      |
| SSH servis       | `systemctl status ssh/sshd`    | active/running           | Servis yok veya stopped            |
| SSH portu        | `ss -tulpen \| grep :22`       | Port 22 LISTEN           | SSH dinlemiyor                     |
| Firewall         | `firewall-cmd --list-all`      | SSH izinli               | Firewall engelliyor                |
| Disk             | `lsblk`, `df -h`               | Planla uyumlu            | Yanlış partition                   |
| Hedef alan       | `df -h /srv/images`            | Yeterli boş alan         | Disk dolu                          |
| Paket yöneticisi | `dnf makecache` / `apt update` | Repo erişimi var         | DNS/repo sorunu                    |
| Failed servis    | `systemctl --failed`           | Failed servis yok        | Başarısız unit var                 |
| Error log        | `journalctl -p err -b`         | Kritik hata yok          | Boot/service hatası                |
| Checksum         | `sha256sum -c file.sha256`     | `OK`                     | Dosya bozuk/eksik                  |

---
