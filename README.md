# Canias ERP Web Servis Araç Seti

Canias ERP'ye dış sistemlerden (Python, Node.js, n8n) kayıt açabilmek için yazılmış özel TROIA web servisleri, SOAP istemcisi ve geliştirme rehberi.

> Bu depo bir proje vitrinidir. Kaynak kod paylaşılmamaktadır.

## Mimari

```
Dış sistem (Python / Node / n8n)
      │  SOAP (login → callService → logout)
      ▼
CaniasWS (Tomcat)
      │  ServiceId → TROIA sınıfı + fonksiyonu
      ▼
TROIA fonksiyonu
      │  ERP'nin kendi iş sınıflarını, ekranda elle yapılan sırayla çağırır
      ▼
PostgreSQL
```

## Yaklaşım

Web servis yeni bir iş mantığı yazmaz. Bir ERP ekranında elle yapılan işlem, ekranın **trace** kaydı incelenerek aynı sınıf metotlarının aynı sırayla çağrılmasıyla kopyalanır. Böylece ekrandaki tüm kontroller ve muhasebe kayıtları korunur.

## Kapsam

- Sipariş, irsaliye, tahsilat fişi ve cari kart oluşturma ve güncelleme servisleri
- Gelen e-fatura ve e-irsaliyeleri alma servisi
- `|` ayrımlı, ayrıştırılması kolay ortak dönüş protokolü
- Node.js SOAP istemcisi (yerleşik `fetch`, bağımlılıksız)
- Trace dosyalarından servis çıkarma rehberi (yapay zekâ destekli geliştirme için ajan dokümanı)
- n8n akışları için muhasebe ve tahsilat sınıflandırma promptları

## Teknolojiler

`TROIA` · `Canias ERP` · `SOAP` · `Node.js` · `Python` · `n8n` · `LLM prompt tasarımı`
