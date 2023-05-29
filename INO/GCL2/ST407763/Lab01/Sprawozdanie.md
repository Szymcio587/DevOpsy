Laboratorium 1

1. Zainstalowałem Gita na Ubuntu - wystarczyło wklepać 2 komendy, zero większej filozofii

![](https://s3.hedgedoc.org/demo/uploads/32154ecb-5703-4581-8cb7-9351c2854447.png)
2. Sklonowałem repo z wykorzystaniem HTTPS. Dużą zaletą HTTPS nad SSH jest łatwość użycia - nie potrzeba żadnego przygotowania aby pobrać jakąś zawartość, przez co content jest szerzej dostępny, oraz nie ma problemów z różnymi firewallami, co nie jest rzeczą oczywistą w przypadku SSH
![](https://s3.hedgedoc.org/demo/uploads/e377f26d-7853-417e-8e1d-a45f0a9ca96a.png)
3. To samo tylko z SSH. Najpierw utworzyłem sobie dwa klucze różnymi metodami: ed25519 oraz ecdsa. Wymagane było podanie hasła do przynajmniej jednego z nich, w moim przypadku był to ecdsa. Obrazy wygenerowały się prawidłowo, klucze działały, więc można uznać ten krok za udany. Z wykorzystaniem tych kluczy nie było problemu z ponownym pobraniem contentu z repo korzystając standardowo z git clone.

![](https://s3.hedgedoc.org/demo/uploads/6b34d2d7-f61c-4b93-b2c3-3d31ee3e22c3.png)
![](https://s3.hedgedoc.org/demo/uploads/984f62fd-9097-43c5-b3cb-4e7097092d02.png)
![](https://s3.hedgedoc.org/demo/uploads/35992f9e-c968-435f-8485-a415de93bb7e.png)
![](https://s3.hedgedoc.org/demo/uploads/841eb13a-ecea-4898-a82f-58ea6e5cf82e.png)

4/5. Tworzenie nowego brancha. Sprowadza się znowu do wklepania jednej komendy git checkout -b nazwa_brancha. Prefiks -b pozwala na utworzenie nowej gałęzi, natomiast jej brak pozwala na poruszanie się pomiędzy gałęziami już istniejącymi.
![](https://s3.hedgedoc.org/demo/uploads/e2379224-5aed-4daa-828c-10b1b825195e.png)


6. Główna gwiazda pierwszych laboratoriów: Git hook. Na chwilę obecną ciężko powiedzieć czy działa, gdyż commita mam utworzyć dopiero po napisaniu tego sprawozdania, natomiast z tego co udało mi się znaleźć w internecie zawartość pliku powinna wyglądać mniej więcej następjąco:
7. 
![](https://s3.hedgedoc.org/demo/uploads/0e1cac53-65b2-4dc9-922f-fdb71d40ddbe.png)


Skrypt jest napisany w Bashu, gdyż jest zarówno dość prosty dla takich podstawowych zastosowań, jak i wydajny

Sam skrypt jedynie pobiera treść commita, i przed nią wyświetla dodatkowy tekst ze zmiennej TICKET.

Po wykonaniu tych kroków, podjąłem próbę spushowania tego tworu na gita i zakończyła się sukcesem

![](https://s3.hedgedoc.org/demo/uploads/423bc0c8-6302-481e-9339-ed7a21de9d43.png)

Jak widać, zgodnie z oczekiwaniami po wpisaniu git commit oprócz nazwy wpisanej po parametrze -m, widnieje także ustawiony nasztywno napis z hooka.

Laboratorium 2

1. Instalacja Dockera przebiegła dość gładko, aczkolwiek niestety nie dokumentowałem na bieżąco tego procesu więc nie jestem pewien czy uwieczniłem wszystkie kroki. Udało mi się zachować z tego taki fragment:

![](https://s3.hedgedoc.org/demo/uploads/8a9de27f-a5d1-4a10-b9c8-93b08e96bc45.png)

2. Już wcześniej byłem zarejestrowany na DockerHub, także ten krok pominąłem

3/4. Wszystkie obrazy udało się pobrać bez problemów. Uruchomienie busyboxa dało mi dostęp do shellowej powłoki, natomiast nie rozumiem z treści polecenia co miałem tam zrobić, tak samo jak ominąłem cały punkt 5 z tego samego powodu. Próbowałem znaleźć jakąś pomoc w internecie o co może chodzić, aczkolwiek nie pomogło mi to.

![](https://s3.hedgedoc.org/demo/uploads/6a8c8c9f-ffbe-4c2a-854e-c047b00024f8.png)

![](https://s3.hedgedoc.org/demo/uploads/5cabef16-828d-45c5-aa19-5fa96128f1da.png)

6. Stworzenie Dockefile nie było zbyt skomplikowane, wystarczyło bowiem zainstalować gita i uruchomić go wywołując instrukcję clone, tak jak na poprzednich ćwiczeniach. W finalnej wersji musiałem dodać sudo apt -y install git, gdyż bez tego parametru proces się zatrzymywał, a na zdjęciu jest opcja bez ponieważ nie chciało mi się robić drugiego zdjęcia. 
 
 ![](https://s3.hedgedoc.org/demo/uploads/01c2ab12-aa94-42d3-b0e1-f0fac1ffeec1.png)
 
 ![](https://s3.hedgedoc.org/demo/uploads/415bc136-9380-4f99-8fdc-f64efe6fc06b.png)

7. Po wykonaniu tych wszystkich poleceń moje działające kontenery zostały przedstawione na zdjęciu powyżej.

8. Czyszczenie obrazów udało się zawrzeć w pięknej dwuelementowej komendzie, kolejno przekazującej wszystkie uruchomione kontenery w celu ich likwidacji przy użyciu intuicyjnego docker kill

![](https://s3.hedgedoc.org/demo/uploads/761e16ed-e204-47c5-9ed7-5c95e8a37978.png)









