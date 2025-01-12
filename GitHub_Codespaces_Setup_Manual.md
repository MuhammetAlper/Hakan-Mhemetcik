

# GitHub Codespaces Setup Manual

Bu kılavuz, GitHub Codespaces kullanarak R ve Quarto ile çalışmaya başlarken karşılaşılabilecek yaygın sorunların çözümlerini adım adım açıklamaktadır.

## 1. GitHub Codespaces'i Başlatma

### Adımlar:
1. Repository’ye Erişim: GitHub hesabınıza giriş yapın ve ders repository’sine erişin. Örneğin:  
   [IST2083 GitHub Repository](https://github.com/HakanMehmetcik/IST2083.git)
2. Codespace’i Açın: Repository sayfasında "Code" butonuna tıklayın, ardından "Open with Codespaces" seçeneğini seçin.
3. Yeni Bir Codespace Oluşturun: Eğer Codespace yoksa, "Create Codespace on main" seçeneğine tıklayarak bir geliştirme ortamı oluşturun.

---

## 2. Quarto CLI Kurulumu

### Sorun: "Please install the Quarto CLI before rendering documents."
Açıklama: GitHub Codespaces, varsayılan olarak Quarto CLI yüklü gelmeyebilir. Quarto CLI'ı kurmanız gerekir.

### Çözüm:
1. Terminali Açın: GitHub Codespaces ortamınızda terminali açmak için View > Terminal seçeneğini kullanın.
2. Quarto CLI’ı İndirin ve Kurun:
   - Quarto’yu kurmak için aşağıdaki komutları çalıştırın:
     ```bash
     # Quarto CLI’ı indirin
     wget https://quarto.org/download/latest/quarto-linux-amd64.deb
     
     # Quarto CLI'ı yükleyin
     sudo dpkg -i quarto-linux-amd64.deb
     ```
3. Kurulumu Kontrol Edin:
   - Quarto'nun kurulduğunu doğrulamak için şu komutu kullanın:
     ```bash
     quarto --version
     ```

---

## 3. R Dili Kurulumu

### Sorun: "could not find R path" hatası
Açıklama: GitHub Codespaces ortamında R dilinin kurulu olmaması bu hataya neden olabilir.

### Çözüm:
1. R'ın Kurulu Olup Olmadığını Kontrol Edin:
   - Terminalde şu komutu çalıştırarak R'ın yüklü olup olmadığını kontrol edin:
     ```bash
     R --version
     ```
2. R’ı Yükleyin:
   - Eğer R kurulu değilse, aşağıdaki komutlarla R'ı yükleyin:
     ```bash
     sudo apt update
     sudo apt install r-base
     ```
3. R'ı Başlatın:
   - R'ı başlatmak için terminalde `R` komutunu yazabilirsiniz:
     ```bash
     R
     ```

---

## 4. Quarto Belgelerini Çalıştırma

### Sorun: Quarto dosyaları çalıştırılamıyor veya render edilmiyor
Açıklama: Quarto ve R birlikte çalışacak şekilde düzgün yapılandırılmamış olabilir.

### Çözüm:
1. R’ın Quarto Tarafından Tanındığını Kontrol Edin:
   - Terminalde şu komutu çalıştırarak Quarto’nun R'ı bulabildiğini doğrulayın:
     ```bash
     quarto check install
     ```
2. Quarto Dosyasını Render Etme:
   - Bir `.qmd` dosyasını render etmek için terminalde aşağıdaki komutu kullanın:
     ```bash
     quarto render dosya-adı.qmd
     ```

---

## 5. Hata Mesajlarını Çözme

### Genel İpuçları:
1. Hata Mesajlarını Dikkatle Okuyun: Hata mesajları size neyin yanlış olduğunu söyler. Mesajdaki detaylara dikkat edin ve eksik kütüphane veya komut hatalarına odaklanın.
2. Kod Bloklarını Tek Tek Test Edin: Özellikle uzun bir kod dizisinde hata alıyorsanız, kod bloklarını tek tek çalıştırarak sorunun nerede olduğunu bulun.
3. R Paketlerini Güncelleyin: Kullandığınız paketlerin güncel olduğundan emin olun. Aşağıdaki komutu kullanarak tüm paketlerinizi güncelleyebilirsiniz:
   ```r
   update.packages()
   ```

---

## 6. R Paketleri ile Çalışma

### Sorun: R paketlerini yükleyemiyorum
Açıklama: GitHub Codespaces ortamında gerekli R paketleri yüklü olmayabilir.

### Çözüm:
1. Bir R paketini yüklemek için:
   ```r
   install.packages("paket-adi")
   ```
2. Paketi yükledikten sonra çalıştırmak için:
   ```r
   library(paket-adi)
   ```

---

## Sonuç

Bu kılavuz, GitHub Codespaces ile R ve Quarto kullanırken karşılaşabileceğiniz sorunları çözmeye yardımcı olmak için tasarlandı. Herhangi bir sorun yaşarsanız, hata mesajlarını dikkatlice okuyarak bu adımları takip edebilir ve çözüm bulabilirsiniz. Eğer sorununuz devam ederse, öğretim üyesi veya asistanınıza başvurun.
