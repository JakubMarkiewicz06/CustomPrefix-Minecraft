# Jak zrobić custom prefixy na serwerze minecraft za pomocą Resource Packa?

Jest to bardzo proste, a co pewnie ważne dla dużego grona osób, nie potrzeba do tego żadnego pluginu!
Pierwszym krokiem będzie stworzenie textur, możesz je zrobic za pomocą dowolnego programu graficznego.

Maksymalny wymiar pliku: 240x240 

# Dla przykładu stworze 2 proste textury, gracza, oraz vipa:

W przypadku rangi gracza użyłem wymiarów:
70x18 ![obraz](https://github.com/JakubMarkiewicz06/CustomPrefix-Minecraft/assets/95700388/1fbb9718-714c-49bc-9c3f-8ff79b628205)

W przypadku vipa użyłem wymiarów:
40x18

![obraz](https://github.com/JakubMarkiewicz06/CustomPrefix-Minecraft/assets/95700388/8e267367-bf99-4edf-b69b-a32b913588ce)


Tak, wiem, że to nie jest najładniejsze...

# Dobra, ale co teraz zrobić jak mam zrobione textury?
Pobierasz Resource Packa którego wysłałem wyżej, otwierasz go i przechodzisz do: assets/jakubprefix/textures/prefix i wrzucasz tam stworzone przez ciebie textury.

Kolejnym krokiem będzie przejście do pliku "default.json" którego znajdziesz w: assets/minecraft/font i go otwierasz

Znajdziesz w nim text w którym możesz podmienić dany znak na wybrany przez ciebie obraz, możesz do tego celu użyć dowolnej czcionki, lub emotki, tak naprawdę to to nie ma znaczenia, ważne żebyś się trzymał tego formatu co ja:

[Strona z przykładowymi znakami](https://jrgraphix.net/r/Unicode/E000-F8FF)
```
{
    "providers": [
        {
            "type": "bitmap",
            "file": "jakubprefix:prefix/vip.png",
            "ascent": 7,
            "height": 7,
            "chars": [""]
        },        {
            "type": "bitmap",
            "file": "jakubprefix:prefix/gracz.png",
            "ascent": 7,
            "height": 7,
            "chars": [""]
        }
    ]
}

```
# Na czym polegają linie: "ascent", oraz "height"?


Odpowiadają one za wielkość wyświetlanego obrazu (zalecana wartość 7/8)

Domyślna wartość w moim Resource Packu:

![obraz](https://github.com/JakubMarkiewicz06/CustomPrefix-Minecraft/assets/95700388/c5b7cf9b-d69a-431d-a96d-a1ea93b8f6dc)

Zmieniona wartość na 

"ascent": 10
"height": 12

![obraz](https://github.com/JakubMarkiewicz06/CustomPrefix-Minecraft/assets/95700388/c8167cdf-6c63-4089-9fab-c6cbacc59e2f)

(Pamiętaj, aby nie robić zbyt dużej przepaści między nimi: przykładowo "ascent" nie może być ustawione na 10, gdy "height" jest ustawione na 6 )
Gdy wartośc ma zbyt dużą przepaść między sobą textura zostaje usunięta:

![obraz](https://github.com/JakubMarkiewicz06/CustomPrefix-Minecraft/assets/95700388/d92c7ae7-23c8-4dc7-b5ca-35c7cf94e2b4)


# Dobrze, a więc z tworzenia Resource Packa to już tyle!

Teraz musimy wrzucić nasz Resource Pack na hosting, w moim przypadku to będzie strona: https://mc-packs.net/ 
**Pamiętaj aby Resource Pack był zapakowany w pliku .zip!!**

Po wrzuceniu Resource Packa na hosting wchodzimy teraz do plików serwera minecraft i szukamy pliku: server.properties, po odpaleniu go interesują nas 2 linijki:
require-resource-pack=false
oraz
resource-pack=

W przypadku pierwszej linijki, zamieniamy wartość false, na true, dzięki niej Resource Pack będzie wymagany do wejścia na serwer.

require-resource-pack=true

W przypadku drugiej wklejamy link do naszego Resource Packa.

resource-pack=https://download.mc-packs.net/pack/347a920a440a682caeaaaecf4cdecbb158c63c92.zip

Po zapisaniu zmian restartujemy serwer.

Teraz jedynie co nam zostało to ustwienie prefixu dla wybranej rangi, w tym celu przechodzimy do pliku w naszym Resource Packu: assets/minecraft/font i kopiujemy znak który wcześniej wybraliśmy, teraz go wystarczy wpisać komendę:
/lp group ranga meta setprefix 101 "&f(znak specjalny) " i gotowe!

![obraz](https://github.com/JakubMarkiewicz06/CustomPrefix-Minecraft/assets/95700388/1291f328-7de8-4757-a6c7-b4ae898eb7b9)

**Pamiętaj, aby przed prefixem był zawsze biały kolor &r/&f, w innym przypadku prefix zostanie zabarwiony:**
![obraz](https://github.com/JakubMarkiewicz06/CustomPrefix-Minecraft/assets/95700388/811b8223-762e-49eb-9ca0-f4983e28397c)


# Dodatkowa informacja
Jest szansa, na to, że gracze odkryją znak specjalny którego uzyłeś do zmiany prefixu i będą nim spamić, w takim wypadku jedynie wystarczy użyć dowolnego pluginu na blokadę słów, np [chatmanagera](https://www.spigotmc.org/resources/chat-manager-1-8-1-20-30-features-and-40-commands.52245/ )




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

 




