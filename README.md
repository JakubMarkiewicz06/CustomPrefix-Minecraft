# Jak zrobić custom prefixy na serwerze minecraft za pomocą Resource Packa?

Jest to bardzo proste, a co pewnie ważne dla dużego grona osób, nie potrzeba do tego żadnego pluginu!
Pierwym krokiem będzie utworzenie stworzenie textur, możesz je zrobic za pomocą dowolnego programu graficznego.

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

# Dobrze, a więc z tworzenia Resource Packa to już tyle!

Teraz musimy wrzucić nasz Resource Pack na hosnting, w moim przypadku to będzie strona: https://mc-packs.net/ 
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

Teraz jedynie co nam zostało to ustwienie prefixu dla danej wybranej rangi, w tym celu przechodzimy do pliku w naszym Resource Packu: assets/minecraft/font i kopiujemy znak który wcześniej wybraliśmy, teraz go wystarczy wpisać komendę:
/lp group ranga meta setprefix 101 "&f(znak specjalny) " i gotowe!

![obraz](https://github.com/JakubMarkiewicz06/CustomPrefix-Minecraft/assets/95700388/0fa8a410-5550-4e22-8760-6f08b8eb3277)

**Pamiętaj, aby przed prefixem był zawsze biały kolor &r/&f, w innym przypadku prefix zostanie zabarwiony:**
![obraz](https://github.com/JakubMarkiewicz06/CustomPrefix-Minecraft/assets/95700388/c3d1d8bf-95b4-43f4-aea8-04e349fad4e3)


# Dodatkowa informacja
Jest szansa, na to, że gracze odkryją znak specjalny którego uzyłeś do zmiany prefixu i będą nim spamić, w takim wypadku jedynie wystarczy użyć dowolnego pluginu na blokadę słów, np [chatmanagera](https://www.spigotmc.org/resources/chat-manager-1-8-1-20-30-features-and-40-commands.52245/ )




 




