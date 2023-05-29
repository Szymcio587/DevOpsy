<h1>Laboratorium nr. 3</h1>
<ol>
    <li>
        Na początek należało wybrać projekt, na bazie którego chcemy wykonać dalsze instrukcje. Ja zdecydowałem się pracować na jednym z przykładów podanych na zajęciach, 
        o nazwie <a href="Screenshot from 2023-04-03 14-21-48.png">LastCalc</a>. Nie wiem dokładnie co robi ten program, natomiast wiedza o istnieniu w nim testów jest wystarczająca aby dało się wykonać z nim wszelkie niezbędne czynności. 
        <img title="t" name="n" src="../Lab03/Screenshot from 2023-04-03 14-21-48.png"/>
        <img title="t" name="n" src="../Lab03/Screenshot from 2023-04-03 14-22-07.png"/>
        Jak widać, testy przeszły bez większych problemów.
    </li>
    <li>
        Następnie, uruchomiłem kontener z fedorą, i to na niej próbowałem uruchomić ww testy.  
        <img title="t" name="n" src="../Lab03/Screenshot from 2023-04-03 15-50-05.png"/>
        Z pobraniem projektu również nie było problemu, instalacja gita przy pomocy yum przeszła bezproblemowo.
        <img title="t" name="n" src="../Lab03/Screenshot from 2023-04-03 17-35-38.png"/>
        W celu uruchomienia projektu musiałem zainstalować jeszcze mavena, lecz jak się okazało nie jest to możliwe przez yuma, więc skorzystałem z dnf.
        <img title="t" name="n" src="../Lab03/Screenshot from 2023-04-03 17-36-05.png"/>
        Plan udał się częściowo: projekt co prawda uruchomił się, i nawet udało się wykonać wszystkie testy tak, jak poza kontenerem, jednakże pod koniec otrzymałem informację iż nie udało się zbudować projektu. Mimo starań nie udało mi się znaleźć przyczyny takiego stanu rzeczy.
        <img title="t" name="n" src="../Lab03/Screenshot from 2023-04-03 17-44-07.png"/>
        <img title="t" name="n" src="../Lab03/Screenshot from 2023-04-03 17-45-34.png"/>
        <img title="t" name="n" src="../Lab03/Screenshot from 2023-04-03 17-45-52.png"/>
    </li>
    <li>
        Ostatnią rzeczą było utworzenie dwóch Dockerfileów w celu zautomatyzowania całego procesu. Wydawało się to dość proste do zrobienia, wszak niewiele instrukcji wykorzystałem aby uruchomić testy. W praktyce, udało mi się stworzyć i pomyślnie uruchomić pierwszy z nich, przygotowujący projekt do uruchomienia:
        <div>
        <br/>FROM ubuntu
        <br/>RUN apt update
        <br/>RUN apt install git -y && apt install maven -y
        <br/>RUN git clone https://github.com/sanity/LastCalc.git 
        <br/>RUN cd LastCalc
        </div>
        <br/>Drugi natomiast z jakiegoś powodu nie uruchamiał poprawnie programu. Logi które mi się wyświetliły nie były szczególnie rozbudowane, więc zakładam że nie jest to ten sam błąd jaki napotkałem w kontenerze, tylko coś popsuło się jeszcze wcześniej podczas próby uruchomienia programu, niestety na to też nie znalazłem skutecznej recepty:
        <div>
        <br/>FROM maven
        <br/>RUN mvn appengine:devserver
        </div>
        <br/><img title="t" name="n" src="../Lab03/Screenshot from 2023-04-08 17-55-13.png"/>
        <img title="t" name="n" src="../Lab03/Screenshot from 2023-04-08 18-10-56.png"/>
    </li>
</ol>
<h1>Laboratorium nr. 4</h1>
<ol>
    <li>
        Czwarte laboratorium rozpocząłem od przeczytania dokumentacji na temat woluminów. Nie zrobiłem z tego ss, ale mam nadzieję że zostanie mi ten podpunkt mimo wszystko zaliczony.
        <br/> Następnie przystąpiłem do części praktycznej: utworzyłem dwa woluminy, wejściowy i wyjściowy, i uruchomiłem kontener jednocześnie podłączając woluminy do niego
        <img title="t" name="n" src="Screenshot from 2023-04-08 18-29-15.png"/>
        Zainstalowałem ponownie niezbędne rzeczy, sklonowałem repo
        <img title="t" name="n" src="Screenshot from 2023-04-08 18-53-00.png"/>
        Tym razem nawet udało się w pełni zbudować projekt, choć nie dostrzegam konkretnej różnicy pomiędzy tym co robiłem kilka dni wcześniej i wtedy, być może po prostu  bogowie Linuxa byli po mojej stronie tym razem.
        <img title="t" name="n" src="Screenshot from 2023-04-08 19-00-43.png"/>
        <img title="t" name="n" src="Screenshot from 2023-04-08 19-00-55.png"/>
        Jak też widać na zdjęciu wyżej, wszystko zostało zapisane na woluminie wyjściowym
        Zrzutu ekranu pokazującego status woluminów niestety nie mam, ponieważ z jakiegoś powodu nie mogłem go dodać na gicie. Wyskakiwał mi wtedy taki błąd:
        <img title="t" name="n" src="Screenshot from 2023-04-09 13-45-10.png"/>
        Po ręcznym usunięciu podanego zrzutu z katalogu laboratoriów, wszystko działało. Na szczęście po wykonaniu komendy "docker volume inspect volume_out" i tak nie wyskakiwały jakieś niezbędne informacje( a przynajmniej tak to wyglądało), tylko rzeczy typu data utworzenia czy przypisane labele, więc bez tego może też jakoś się obejdzie 
    </li>
    <li>
        Kolejny segment również rozpoczął się od gorliwego przeglądania dokumentacji, z których chyba jednak niewiele zrozumiałem bo nie byłem w stanie się nadal połączyć, więc musiałem bazować na filmikach znalezionych w odmętach YouTuba. Zgodnie z zaleceniami, w kontenerze oprócz instalacji iperf3 dodałem również od razu net-toolsy, gdyż pozwalały one uzyskać adres IP potrzebny do dokonania połączenia.
        <img title="t" name="n" src="Screenshot from 2023-04-09 12-39-08.png"/>
        <img title="t" name="n" src="Screenshot from 2023-04-09 12-39-22.png"/>
        <img title="t" name="n" src="Screenshot from 2023-04-09 12-40-18.png"/>
        Pierwszy test, wykonany w całości z dwóch różnych kontenerów zakończył się pomyślnie, a przynajmniej tak mi się wydaje.
        <img title="t" name="n" src="Screenshot from 2023-04-09 13-00-15.png"/>
        <img title="t" name="n" src="Screenshot from 2023-04-09 13-00-15.png"/>
        Analogiczną czynność wykonałem spoza kontenera, w terminalu Ubuntu:
        <img title="t" name="n" src="Screenshot from 2023-04-09 13-03-06.png"/>
        <img title="t" name="n" src="Screenshot from 2023-04-09 13-03-13.png"/>
        Niestety robiąc instrukcję na te laboratoria patrzyłem na plik .md dla MDO2023_S a nie INO, a tam nie było informacji o network create, więc na chwilę obecną też tego w sprawozdaniu nie zawieram. Odpowiedni update ukaże się na dniach.
    </li>
    <li>
        Ostatnią rzeczą była instalacja Jenkinsa, która to już nie stanowiła wyzwania po poprzednich trudach związanych z pracą w kontenerach. Wszystko udało się zrobić wedle strony, nie napotkałem żadnych przeszkód, a ekran startowy Jenkinsa ukazał się moim oczom w krótkim czasie od rozpoczęcia działań. Poniżej wklejam wszystkie akcje które wykonałem po kolei aby to zrobić.
        <img title="t" name="n" src="Screenshot from 2023-04-09 13-31-22.png"/>
        <img title="t" name="n" src="Screenshot from 2023-04-09 13-31-37.png"/>
        <img title="t" name="n" src="Screenshot from 2023-04-09 13-33-13.png"/>
        <img title="t" name="n" src="Screenshot from 2023-04-09 13-34-09.png"/>
        <img title="t" name="n" src="Screenshot from 2023-04-09 13-38-59.png"/>
        <img title="t" name="n" src="Screenshot from 2023-04-09 13-39-40.png"/>
        <img title="t" name="n" src="Screenshot from 2023-04-09 13-40-46.png"/>
    </li>
</ol>