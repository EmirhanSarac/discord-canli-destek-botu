# Modmail for Discord

# Emirhan Saraç Tarafından Çevirilmiştir
**[Kod Paylaşım Sunucusuna Katıl](https://discord.gg/NPGdsSv)**


A bot for [Discord](https://discordapp.com/) that allows users to DM the bot to contact the server's entire mod team.
These DMs get relayed to a modmail server where each user gets their own channel, or "thread".
Moderators and admins can then reply to these threads, and these responses are relayed back to the original user as a DM.

Inspired by Reddit's modmail system.

## NOTE! If you're upgrading to v2.23.0, note that Node.js 10 is now required at minimum.

## Table of contents

- [Setup](#setup)
- [Support server](#support-server)
- [Changelog](#changelog)
- [Commands](#commands)
  - [Anywhere on the inbox server](#anywhere-on-the-inbox-server)
  - [Inside a modmail thread](#inside-a-modmail-thread)
- [Configuration options](#configuration-options)
- [Plugins](#plugins)
  - [Specifying plugins to load](#specifying-plugins-to-load)
  - [Creating a plugin](#creating-a-plugin)

## Setup

1. Node.js 10 (LTS) veya üstünü yükleyin
2. En son sürümü şuradan indirin: [orijinal Sayfa](https://github.com/Dragory/modmailbot/releases)
3. Modmail gelen kutusu olarak kullanılacak bir Discord sunucusu oluşturun
4. Dosyanın bir kopyasını oluşturun `config.example.json` aynı klasöre kopyalayın ve kopyayı adlandırın `config.json`. Dosyayı açın ve değerleri girin.
   - Bu sayfanın sonunda daha fazla yapılandırılabilir seçenek de bulabilirsiniz!
5. Bağımlılıkları yükle: `npm ci`
6. Sunuculara bot ekleyin ve posta sunucusunda uygun izinleri verdiğinizden emin olun.
7. Botu Çalıştırın: `npm start`

## Support server

If you need help with setting up the bot or would like to discuss other things related to the bot, join the support server on Discord here:

https://discord.gg/vRuhG9R

## Changelog

See [CHANGELOG.md](CHANGELOG.md)

## Commands

### Anywhere on the inbox server

`!logs <user> <page>` Belirtilen kullanıcıyla önceki modmail günlüklerini listeler. Çok sayıda günlük varsa sayfalandırılır. Bu durumda, ikinci argüman olarak görüntülenecek sayfa numarasını belirtebilirsiniz.
`!block <user> <time>` Belirtilen kullanıcının modmail kullanmasını engeller. Bir zaman belirtilirse, blok geçicidir.
`!unblock <user> <time>` Belirtilen kullanıcının modmail kullanmasını engeller. Bir zaman belirtilirse, kullanıcının bu süreden sonra engeli kaldırılacak şekilde zamanlanır.
`!is_blocked <user>` Kullanıcının engellenip engellenmediğini ve ne kadar süreyle kontrol edileceğini kontrol eder
`!s <shortcut> <text>` Parçacık ekler (hazır yanıt). Bağımsız değişkenler için {1}, {2} vb. Desteği. Nasıl kullanılacağı için aşağıya bakın.
`!edit_snippet <shortcut> <text>` Mevcut bir snippet'i düzenler (ek `!es`)  
`!delete_snippet <shortcut>` Belirtilen snippet'i siler (Ek `!ds`)  
`!snippets` Kullanılabilir tüm parçacıkları listeler
`!version` Çalıştırdığınız botun sürümünü yazdırır
`!newthread <user>` Belirtilen kullanıcıyla yeni bir ileti dizisi açar

### Inside a modmail thread

`!reply <text>` Kullanıcıya "(Rol) Kullanıcı: metin" biçiminde bir yanıt gönderir(alias `!r`)  
`!anonreply <text>` Kullanıcıya "Rol: metin" biçiminde anonim bir yanıt gönderir" (alias `!ar`)  
`!close <time>` Modmail iş parçacığını kapatır. Bir zaman belirtilirse, iş parçacığının daha sonra kapatılması planlanır. Kullanıcıya bir mesaj gönderilir veya gönderilirse, programlı kapanma iptal edilir.
`!logs <page>` Bu kullanıcıyla önceki modmail günlüklerini listeler. Çok sayıda günlük varsa sayfalandırılır. Bu durumda, bağımsız değişken olarak görüntülenecek sayfa numarasını belirtebilirsiniz.
`!block <time>` Kullanıcının modmail kullanmasını engeller. Bir zaman belirtilirse, blok geçicidir.
`!unblock <time>` Kullanıcının modmail kullanmasını engeller. Bir zaman belirtilirse, kullanıcının bu süreden sonra engeli kaldırılacak şekilde zamanlanır.
`!!shortcut` Bir pasajla cevap verin. Kısayolu, parçacıkların gerçek kısayollarıyla değiştirin.
`!!!shortcut` Snippet ile anonim olarak yanıtlayın. Kısayolu pasajın gerçek kısayoluyla değiştirin.
`!move <category>` `AllowMove` etkinse, iş parçacığı kanalını belirtilen kategoriye taşır
`!loglink` Geçerli iş parçacığının günlüğüne bağlantı gösterir
`!suspend` Bir iş parçacığını askıya alın. İleti dizisi kapalı olarak işlev görür ve askıya alınmadıkça hiçbir ileti almaz.
`!unsuspend` Bir iş parçacığını askıya alma
`!id` Kullanıcının kimliğini yazdırır
`!alert` İş parçacığı yeni bir yanıt aldığında sizi pingler. İptal etmek için `!Alert cancel` düğmesini kullanın.

Kullanmadan otomatik olarak cevaplamak için !reply ve !r, enable `alwaysReply` yapılandırmada. `alwaysReplyAnon` anonim olarak yanıt verip vermemeyi ayarlar. Yanıtlamak istemezseniz, önekte başlayan (varsayılan olarak!) Gibi herhangi bir mesajı yoksayar!

