# OznDefense-Network-System
Tabii, README dosyasını daha kapsamlı ve detaylı hale getirebilirim. Proje hakkında ek bilgiler, kullanım senaryoları, yapılandırma seçenekleri veya örneklerle zenginleştirilmiş bir README hazırlayalım. Aşağıda daha kapsamlı bir versiyon önerisi sunuyorum:

---

# 🛡️ OznDefense Network System

**OznDefense Network System**, ağ güvenliğini sağlamak için geliştirilmiş kapsamlı bir sistemdir. Bu proje, ağ trafiğini analiz ederek ve güvenlik açıklarını belirleyerek veri güvenliğini artırmayı amaçlar. 🔒

## 🚀 Başlarken

Bu kılavuz, OznDefense Network System'i yerel ortamınızda çalıştırmak için gerekli adımları sağlar.

### 📋 Gereksinimler

- 🦀 [Rust](https://www.rust-lang.org/) (1.60 veya üstü)
- 🛠️ [Cargo](https://doc.rust-lang.org/cargo/) (Rust'un paket yöneticisi ve derleyici aracı)

### 🚀 Kurulum

1. Depoyu klonlayın:
    ```bash
    git clone https://github.com/ibrahimsql/OznDefense-Network-System.git
    ```

2. Proje dizinine gidin:
    ```bash
    cd OznDefense-Network-System
    ```

3. Bağımlılıkları yükleyin ve projeyi derleyin:
    ```bash
    cargo build --release
    ```

4. Derlenmiş binary'i çalıştırın:
    ```bash
    ./target/release/ozn_defense
    ```

## 🏃 Kullanım

Projeyi başlatmak ve kullanmak için aşağıdaki adımları izleyin:

1. **Sunucuyu başlatın**:
    ```bash
    cargo run --release
    ```

2. **Ağ trafiğini analiz edin**:
    Proje arayüzünden ağ trafiğini izlemeye başlayabilirsiniz. Web arayüzü veya komut satırı arayüzü aracılığıyla analiz yapabilirsiniz.

### Konfigürasyon

OznDefense Network System, çeşitli yapılandırma seçenekleri sunar. `config.toml` dosyasını düzenleyerek ayarları yapılandırabilirsiniz.

#### Örnek `config.toml` Dosyası:

```toml
[server]
host = "0.0.0.0"
port = 8080

[logging]
level = "info"
```

### Örnek Komutlar

- Trafik analizini başlatma:
    ```bash
    cargo run --release -- analyze_traffic
    ```

- Rapor oluşturma:
    ```bash
    cargo run --release -- generate_report
    ```
- 1. Handshake Capture (El Sıkışma Yakalama)
Bu mod, bir Wi-Fi ağına bağlanan cihazların el sıkışmalarını yakalar. WPA/WPA2 şifrelerini kırmak için kullanılır.

cargo run -- --mode handshake_capture --interface wlan0 --target_bssid AA:BB:CC:DD:EE:FF --packet_count 100
--mode handshake_capture: El sıkışma yakalama modunu seçer.
--target_bssid AA:BB:CC:DD:EE:FF: Hedefin BSSID'si.
--packet_count 100: Yakalamak için gönderilecek paket sayısı.


-2. Beacon Flooding
Bu mod, sahte erişim noktaları oluşturarak Wi-Fi tarayıcılarını yanıltır ve gerçek erişim noktalarını gizler.

cargo run -- --mode beacon_flood --interface wlan0 --packet_count 500 --target_ssid_prefix "FakeAP_"
--mode beacon_flood: Beacon flood saldırı modunu seçer.
--packet_count 500: Gönderilecek beacon paketi sayısı.
--target_ssid_prefix "FakeAP_": Sahte SSID'lerin ön eki.

-3. Evil Twin Attack
Bu saldırı, bir kullanıcıyı sahte bir erişim noktasına bağlamaya çalışır.
cargo run -- --mode evil_twin --interface wlan0 --target_ssid "TargetSSID" --deauth_all true --log_path /path/to/log.txt

--mode evil_twin: Evil Twin saldırı modunu seçer.
--target_ssid "TargetSSID": Hedef SSID adı.
--deauth_all true: Tüm istemcileri hedef alır.
--log_path /path/to/log.txt: Kayıt dosyasının yolu.



-4. PMKID Attack
PMKID, WPA/WPA2 ağlarında bir tür el sıkışma yakalama yöntemidir. Bu komut PMKID'leri yakalamaya yöneliktir. 
cargo run -- --mode pmkid_attack --interface wlan0 --target_bssid AA:BB:CC:DD:EE:FF --verbosity 3
--mode pmkid_attack: PMKID saldırı modunu seçer.
--target_bssid AA:BB:CC:DD:EE:FF: Hedef BSSID.
--verbosity 3: Çıktının detay seviyesini belirler.

-5. Bruteforce WPA/WPA2 Attack
Bu saldırı, WPA/WPA2 şifrelerini brute-force yöntemiyle kırmaya çalışır.

cargo run -- --mode wpa_crack --interface wlan0 --dictionary_path /path/to/dictionary.txt --target_bssid AA:BB:CC:DD:EE:FF --verbosity 2
--mode wpa_crack: WPA/WPA2 şifre kırma modunu seçer.
--dictionary_path /path/to/dictionary.txt: Sözlük dosyasının yolu.
--target_bssid AA:BB:CC:DD:EE:FF: Hedef BSSID.
--verbosity 2: Çıktının detay seviyesini belirler.

-6. Deauthentication Attack for All Clients
Bu saldırı, belirli bir erişim noktasına bağlı tüm cihazları hedef alır ve bağlantılarını kesmeye çalışır.

cargo run -- --mode deauth --interface wlan0 --target_bssid AA:BB:CC:DD:EE:FF --deauth_all true --packet_count 5000
--mode deauth: Deauthentication saldırı modunu seçer.
--deauth_all true: Tüm istemcileri hedef alır.
--packet_count 5000: Gönderilecek paket sayısı.



## 📚 Dokümantasyon

Projenin tam dokümantasyonu [burada](link-to-docs) bulunabilir. Dokümantasyon, kullanım senaryoları, API referansları ve daha fazlasını içerir.

## 🤝 Katkıda Bulunma

Katkılarınız bizim için çok değerlidir! Katkıda bulunmak için:

1. Bu projeyi çatallayın (fork).
2. Kendi değişikliklerinizi yapın ve bir pull request açın.
3. Yapmak istediğiniz değişiklikleri açıklayın.

Lütfen katkıda bulunmadan önce `CONTRIBUTING.md` dosyasını inceleyin.

## 📜 Lisans

Bu proje [Lisans Adı] lisansı altında lisanslanmıştır. Daha fazla bilgi için `LICENSE` dosyasına bakabilirsiniz.

## 🌟 İletişim

Sorularınız veya geri bildirimleriniz için [e-posta adresi] veya [geliştirici profili] üzerinden iletişime geçebilirsiniz.

---
