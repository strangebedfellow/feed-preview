
# Utwórz komponent/widżet podglądu treści kanału RSS
 
Po zakończeniu udostępnij adres repozytorium git z utworzonym widżetem
 
## Opcja A (preferowana) - Jako komponent tej aplikacji Vue
 
Więcej informacji o aplikacji w tym repozytorium w pliku [README](README.md)
 
1. Utwórz komponent o nazwie FeedPreview.
2. Komponent jako argument props `url` przyjmuje url do kanału RSS.
3. Komponent ma wyświetlać podgląd aktualnych treści w kanale RSS.
4. Widok ma być ostylowany tak, aby był przyjazny dla internauty.
5. Funkcja szukania. 
Komponent ma posiadać pole input do szukania wśród wpisów.
Szukanie ma się odbywać po tytule wpisu w kanale RSS.
6. Komponent ma być do użycia przez kod:
   ```html
   <feed-preview :url="https://www.gamespot.com/feeds/mashup/"></feed-preview>
   ```
7. Kiedy nie można pobrać danych pod danym adresem url, ma się wyświetlić komunikat o błędzie i przycisk do ponowienia pobrania.
 
## Opcja B (alternatywna) - Nie Vue
 
Widżet może być stworzony z wykorzystaniem innych technologii/frameworków np. react, angular, vanilla-js.
Z wytycznymi takimi jak w Opcji A.
