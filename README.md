This project has been created as part of the 42 curriculum by seguler.
libft
Description
Bu proje, 42 müfredatındaki ilk büyük C projesi olan libft çalışmasıdır.
Amaç, C standard library (libc) içindeki birçok temel fonksiyonu sıfırdan yazarak kendi statik kütüphanemi (libft.a) oluşturmaktır.
Bu proje sayesinde:

bellek yönetimi (malloc/free)
pointer aritmetiği
string işlemleri
defensive programming
edge case yönetimi (NULL, overflow, boş string, allocation fail)
norm kuralları

gibi konularda derinlemesine pratik kazanılmıştır.
Bu kütüphane, ilerideki 42 projelerinde kullanılacak kişisel bir araç seti (toolkit) olarak tasarlanmıştır.

Detailed Library Description
Part 1 — Libc Fonksiyonları
Standart C fonksiyonlarının ft_ prefix'i ile yeniden yazılmış halleri:
Karakter kontrolleri

ft_isalpha — alfabetik karakter kontrolü
ft_isdigit — rakam kontrolü
ft_isalnum — alfanümerik karakter kontrolü
ft_isascii — ASCII karakter kontrolü
ft_isprint — yazdırılabilir karakter kontrolü

String işlemleri

ft_strlen — string uzunluğu
ft_strchr — karakterin ilk konumu
ft_strrchr — karakterin son konumu
ft_strncmp — string karşılaştırma
ft_strnstr — substring arama
ft_atoi — string → integer dönüşümü

Memory işlemleri

ft_memset — belleği belirtilen byte ile doldurur
ft_bzero — belleği sıfırlar
ft_memcpy — bellek kopyalama (overlap yok)
ft_memmove — bellek kopyalama (overlap güvenli)
ft_memchr — bellekte byte arama
ft_memcmp — bellek karşılaştırma

String kopyalama

ft_strlcpy — güvenli string kopyalama
ft_strlcat — güvenli string birleştirme

Dönüşüm ve dinamik bellek

ft_toupper — büyük harfe çevirme
ft_tolower — küçük harfe çevirme
ft_calloc — bellek tahsisi ve sıfırlama
ft_strdup — string kopyalama (dinamik)


Part 2 — Ek Fonksiyonlar
Libc'de olmayan yardımcı fonksiyonlar:

ft_substr — string'den parça çıkarır
ft_strjoin — iki string'i birleştirir
ft_strtrim — baştan ve sondan karakter temizler
ft_split — delimiter'a göre string böler (en karmaşık fonksiyon)
ft_itoa — integer → string dönüşümü

Fonksiyonel programlama

ft_strmapi — string'e index + karakter parametreli fonksiyon uygular
ft_striteri — string'e index + pointer parametreli fonksiyon uygular

File descriptor fonksiyonları

ft_putchar_fd — karakteri fd'ye yazar
ft_putstr_fd — string'i fd'ye yazar
ft_putendl_fd — string + newline'ı fd'ye yazar
ft_putnbr_fd — integer'ı fd'ye yazar


Part 3 — Linked List (Bonus)
Bağlı liste (linked list) yapısı:
ctypedef struct s_list
{
    void *content;
    struct s_list *next;
} t_list;
Fonksiyonlar:

ft_lstnew — yeni düğüm oluşturur
ft_lstadd_front — listenin başına ekler
ft_lstadd_back — listenin sonuna ekler
ft_lstsize — liste uzunluğunu döndürür
ft_lstlast — son düğümü döndürür
ft_lstdelone — tek düğüm siler
ft_lstclear — tüm listeyi temizler
ft_lstiter — her düğüme fonksiyon uygular
ft_lstmap — her düğüme fonksiyon uygulayarak yeni liste oluşturur


Instructions
Compilation
bash# Ana kütüphaneyi derle
make

# Object dosyalarını temizle
make clean

# Tüm oluşturulan dosyaları sil
make fclean

# Yeniden derle
make re
Makefile, tüm .c dosyalarını -Wall -Wextra -Werror bayraklarıyla derler ve libft.a statik kütüphanesini oluşturur.
Usage
Kütüphaneyi kendi projenizde kullanmak için:
c#include "libft.h"

int main(void)
{
    char *str = ft_strdup("Hello 42!");
    ft_putendl_fd(str, 1);
    free(str);
    return (0);
}
Derleme:
bashcc main.c -L. -lft -o program
Testing
Proje Windows ortamında geliştirildi, Linux'ta test edildi.
Kullanılan test araçları:
bash# Tripouille tester
make -C ~/libftTester

# Francinette
francinette   

Test sürecinde özellikle şu noktalara dikkat edildi:

NULL pointer kontrolleri
Malloc başarısızlık senaryoları
Edge case'ler (boş string, INT_MIN, INT_MAX)
Memory leak kontrolleri


Resources
Dokümantasyon

Man Pages — Her fonksiyonun resmi dokümantasyonu (temel kaynak)
C Programming Language (K&R) — C dilinin temelleri
GNU C Library Documentation — Libc referansı
Arkadaşlarla tartışmalar — Özellikle karmaşık fonksiyonlar için peer-learning

AI Kullanımı
Subject PDF'i İngilizce olduğu için ve C dilinde yeni başladığım için ChatGPT ve Claude'u yoğun şekilde kullandım:
Kullanım alanları:

Fonksiyon açıklamaları: Subject'teki İngilizce gereksinimleri Türkçe anlamak için kullandım. Her fonksiyonun ne yaptığını, parametrelerinin anlamını, dönüş değerlerini Türkçe açıklatarak kavradım.
Kavramsal farklılıklar: memmove vs memcpy, strlcpy vs strcpy, calloc vs malloc gibi benzer fonksiyonlar arasındaki farkları Türkçe örneklerle öğrendim.
Edge case analizi: Hangi uç durumları test etmem gerektiğini Türkçe açıklamalarla anladım:

NULL pointer kontrolü
Boş string durumları
Integer overflow (INT_MIN, INT_MAX)
Malloc başarısızlık senaryoları


Debugging yardımı: ft_split ve ft_lstmap gibi karmaşık fonksiyonlardaki bellek yönetimi hatalarını anlamak için Türkçe açıklamalar aldım. AI'a direkt "kodu yaz" demedim, "bu mantık doğru mu?" veya "hangi durumları kontrol etmeliyim?" sorularını sordum.
Algoritma mantığı: Özellikle ft_split'in delimiter'a göre string ayırma mantığını ve linked list fonksiyonlarının pointer manipülasyonunu Türkçe örneklerle kavradım.
README formatı: Bu dokümantasyonu 42 subject gereksinimlerine uygun şekilde yapılandırmak için kullandım.

Önemli: Hiçbir fonksiyonun kodu AI tarafından yazılmadı. Tüm implementasyonlar benim tarafımdan manuel olarak yazıldı. AI'ı sadece konseptleri anlamak, Türkçe açıklamalar almak ve öğrenme sürecimi hızlandırmak için kullandım.

Technical Notes

Norm v3 kurallarına tam uyumlu
25 satır limiti ve fonksiyon sayısı kısıtlamalarına uyuldu
Global değişken yok — tüm değişkenler lokal/static
Memory leak yok — tüm malloc'lar kontrol edildi ve free edildi
Platform notları:

strlcpy ve strlcat GNU libc'de varsayılan değil (BSD'de var)
calloc: nmemb veya size = 0 ise free'e güvenli pointer döner
# libft
