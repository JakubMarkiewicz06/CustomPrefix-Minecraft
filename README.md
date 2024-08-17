# Jak zrobić custom prefixy na serwerze minecraft za pomocą Resource Packa?

Jest to bardzo proste, a co pewnie ważne dla dużego grona osób, nie potrzeba do tego żadnego pluginu!
Pierwszym krokiem będzie stworzenie textur, możesz je zrobic za pomocą dowolnego programu graficznego.

Maksymalny wymiar pliku: +/- 450, sprawdź samemu na testowej texturze.

# Dla przykładu stworze 4 proste textury, gracza, vipa, moderatora, oraz właściciela:

W przypadku rangi właściciela użyłem wymiarów:
91x16 ![obraz](https://github.com/user-attachments/assets/806ef04f-92a1-4480-a0c1-245ee7724185)
W przypadku rangi moderatora użyłem wymiarów:
79x16 ![obraz](https://github.com/user-attachments/assets/5cf5a056-3ecd-4968-b1eb-dae54fc78554)
W przypadku rangi vipa użyłem wymiarów:
75x16 ![obraz](https://github.com/user-attachments/assets/80da3696-c153-411e-95df-e80ead225abf)
W przypadku rangi gracza użyłem wymiarów:
87x16 ![obraz](https://github.com/user-attachments/assets/4fdb46a1-31b1-4de5-b3c9-3719414fda27)

# Dobra, ale co teraz zrobić jak mam zrobione textury?
Pobierasz Resource Packa którego wysłałem wyżej, otwierasz go i przechodzisz do: assets/jakubprefix/textures/prefix i wrzucasz tam stworzone przez ciebie textury.

Kolejnym krokiem będzie przejście do pliku "default.json" którego znajdziesz w: assets/minecraft/font i go otwierasz

Znajdziesz w nim plik tekstowy w którym możesz podmienić dany znak na wybrany przez ciebie obraz, możesz do tego celu użyć dowolnej czcionki, lub emotki, tak naprawdę to to nie ma znaczenia, ważne żebyś się trzymał tego formatu co ja:

[Strona z przykładowymi znakami](https://jrgraphix.net/r/Unicode/E000-F8FF)
```
{
    "providers": [
        {
            "type": "bitmap",
            "file": "jakubprefix:prefix/root.png",
            "ascent": 7,
            "height": 8,
            "chars": ["ᜀ"]
        },
        {
            "type": "bitmap",
            "file": "jakubprefix:prefix/moderator.png",
            "ascent": 7,
            "height": 8,
            "chars": ["ᜁ"]
        },
        {
            "type": "bitmap",
            "file": "jakubprefix:prefix/vip.png",
            "ascent": 7,
            "height": 8,
            "chars": ["ᜂ"]
        },
        {
            "type": "bitmap",
            "file": "jakubprefix:prefix/gracz.png",
            "ascent": 7,
            "height": 8,
            "chars": ["ᜃ"]
        }
    ]
}


```
# Na czym polegają linie: "ascent", oraz "height"?


Odpowiadają one za wielkość i położenie wyświetlanego obrazu (zalecana wartość 7/8)

Domyślna wartość w moim Resource Packu:

![obraz](https://github.com/user-attachments/assets/aaa07922-7122-47e5-ab4b-0e9342c1fcec)

Zmieniona wartość na 
"ascent": 10
"height": 12

![obraz](https://github.com/user-attachments/assets/e98e70c5-e33e-41fe-a7a0-63c03fbfac7a)

(Pamiętaj, aby nie robić zbyt dużej wartości rozmiaru i wysokości prefixów: Gdy wartość będzie zbyt duża textura zostanie usunięta.

![obraz](https://github.com/user-attachments/assets/b6741a79-7a0f-4cd5-992c-d071360d8d87)

# Dobrze, a więc z tworzenia Resource Packa to już tyle!

Teraz musimy wrzucić nasz Resource Pack na hosting, w moim przypadku to będzie strona: https://mc-packs.net/ 
**Pamiętaj aby Resource Pack był zapakowany w pliku .zip!!**

Po wrzuceniu Resource Packa na hosting wchodzimy teraz do plików serwera minecraft i szukamy pliku: server.properties, po odpaleniu go interesują nas 3 linijki:
require-resource-pack=false,resource-pack= oraz resource-pack-sha1=

W przypadku pierwszej linijki, zamieniamy wartość false, na true, dzięki niej Resource Pack będzie wymagany do wejścia na serwer.

require-resource-pack=true

W przypadku drugiej wklejamy link do naszego Resource Packa.

resource-pack=https://download.mc-packs.net/pack/baf77fd7bbc3b735975db419368851796885370a.zip

W przypadku trzeciej wklejami ciąg znaków z strony mc-packs

resource-pack-sha1=baf77fd7bbc3b735975db419368851796885370a

Po zapisaniu zmian restartujemy serwer.

Teraz jedynie co nam zostało to ustwienie prefixu dla wybranej rangi, w tym celu przechodzimy do pliku w naszym Resource Packu: assets/minecraft/font i kopiujemy znak który wcześniej wybraliśmy, teraz wystarczy wpisać komendę:
/lp group ranga meta setprefix (waga prefixu) "&f(znak specjalny) " i gotowe!

![obraz](https://github.com/user-attachments/assets/aaa07922-7122-47e5-ab4b-0e9342c1fcec)

**Pamiętaj, aby przed prefixem był zawsze biały kolor &r/&f, w innym przypadku prefix zostanie zabarwiony:**

![obraz](https://github.com/user-attachments/assets/d445d342-a27d-4fa4-a08f-412c91809e8f)


# Dodatkowe informacje
Jest szansa, na to, że gracze odkryją znak specjalny którego uzyłeś do zmiany prefixu i będą nim spamić, w takim wypadku jedynie wystarczy użyć dowolnego pluginu na blokadę słów, np [chatmanagera](https://www.spigotmc.org/resources/chat-manager-1-8-1-20-30-features-and-40-commands.52245/ )

Jeżeli chcesz, aby gracze ładowali texturepack już z poziomu serwera proxy to zainstaluj plugin [forcepack](https://github.com/SamB440/ForcePack/releases). Przydatne, jeżeli masz parę serwerów na sieci i nie chcesz aby gracze ładowali txt za każdym wyjściem/wejściem z trybu. 




# Jak zrobić od zera Resource Pack nie korzystając z przygotowanego przezemnie pliku?

1. Tworzysz folder z nazwą twojego resource packa.
2. Tworzysz w nim plik pack.mcmeta
3. Otwierasz go
4. Wklejasz poniższy tekst i zapisujesz zmiany
```
{
    "pack": {
        "pack_format": 15,
        "description": "Linia 1 \n Linia 2"
    }
}
```
5. Tworzysz folder assets > minecraft > font i tworzysz plik default.json
6. Otwierasz go i wklejasz poniższy tekst i zapisujesz:
```
{
    "providers": [
        {
            "type": "bitmap",
            "file": "(nazwa folderu z punktu 7):prefix/(nazwa rangi z poczatku poradnika.png)",
            "ascent": 7,
            "height": 7,
            "chars": [" Niestandardowy znak z strony podanej wyżej "]
        }        
    ]
}
```
7. Cofasz się do folderu assets i tworzysz folder o dowolnej nazwie, w moim przypadku to będzie "jakubprefix"
8. Tworzysz w nim folder "textures" a w nim folder "prefix"
9. Masz już prawie gotowy Resource Pack, teraz jedynie wystarczy wrzucić textury prefixów do folderu "prefix"


# Gotowy efekt

**ROOT:**

Chat: ![obraz](https://github.com/user-attachments/assets/b0630c8f-5e68-4ad9-9d34-d453994b7e39)
![obraz](https://github.com/user-attachments/assets/194ae9e1-afe2-47ff-8a6e-dfe50b41eea5)

**Moderator:**

Chat: ![obraz](https://github.com/user-attachments/assets/6ae2fd0c-b7c7-43dc-98c5-cbcee73ae05b)
![obraz](https://github.com/user-attachments/assets/87c48843-7a11-437d-8832-25bd952b05f8)



**VIP**

Chat: ![obraz](https://github.com/user-attachments/assets/10fbe01e-cc06-469a-ae0e-7234790439a2)
![obraz](https://github.com/user-attachments/assets/19825068-d740-4de7-a0ff-f4ae1a587d5e)


**Gracz:**

Chat: ![obraz](https://github.com/user-attachments/assets/e7fcd001-b18a-4c04-be7c-25b6d1cf9e9a)
![obraz](https://github.com/user-attachments/assets/63bed32d-220e-4d70-bccd-698583de6789)



