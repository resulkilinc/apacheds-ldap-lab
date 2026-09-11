# ApacheDS LDAP Lab

Apache Directory Server üzerinde kurulan eğitim laboratuvarı: DIT (organizasyon birimleri + kullanıcılar + gruplar), ACL / yetkilendirme, LDAPS ve temel güvenlik testleri.

> Staj defteri ve teslim PDF’leri bu depoda yok. Parolalar lab içindir (`LabOnly-ChangeMe`) — üretimde kullanma.

## Ne var?

| Yol | İçerik |
|-----|--------|
| `ldif/` | Departman, kullanıcı, grup ve ACL örnekleri |
| `assets/` | DIT / UI ekran görüntüleri + lab sertifikası |
| `docs/security-test-RESULTS.txt` | AuthN / AuthZ / TLS test özeti |

## Senaryo

- Alan: `dc=company,dc=local` (kurgusal)
- OU’lar: IT, HR, Finance, Sales, Support, Marketing, Operations…
- Gruplar: IT-Admins, HR-Managers, Finance-Team, …
- ACL: departman bazlı yönetim; `userPassword` normal kullanıcıdan gizlenir
- TLS: LDAPS (ör. 10636) + StartTLS

## Önerilen sıra

1. ApacheDS kur / lab instance başlat
2. Temel DIT’i oluştur
3. `lab-company-30users.ldif` ve grup LDIF’lerini uygula
4. `lab-step2-acl-apache.ldif` (veya hedef sunucuya uygun ACL) ile erişim kontrolünü aç
5. `lab-add-operations-*.ldif` ile sonradan OU ekleme pratiği
6. Bind / yanlış parola / ACL deny / LDAPS testlerini tekrarla

```bash
ldapmodify -H ldap://127.0.0.1:10389 -D "uid=admin,ou=system" -w '***' -f ldif/lab-step2-users.ldif
```

## Güvenlik notları

- LDIF içindeki parolalar bilinçli olarak zayıf lab parolasıdır.
- Sertifika self-signed lab sertifikasıdır.
- Gerçek şirket dizini veya kurumsal sırlar eklenmemiştir.

## Lisans

Eğitim / portföy amaçlı örnek.
