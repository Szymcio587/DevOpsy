<h1>Sprawozdanie z laboratoriów 5-7</h1>
<h2>Pipeline, Jenkins, izolacja etapów</h2>
<h3>Przygotowanie</h3>
<ol>
    Pierwszym krokiem do realizacji ćwiczenia było upewnienie się, że konfiguracja utworzona pod koniec 4 laboratoriów działała prawidłowo. Na poprzednich ćwiczeniach udało mi się już przedstawić proces instalacji tego obrazu, tak więc te laboratoria zacząłem już od momentu uruchomienia Jenkinsa, jak na zdjęciu umieszczonym poniżej:
    <img title="t" name="n" src="../Lab04/Screenshot from 2023-04-09 13-40-46.png"/>
    Ponadto, utworzyłem również nową sieć komendą docker network create docker
    <img title="t" name="n" src="Screeny/Screenshot from 2023-05-07 18-33-04.png"/>
</ol>

<h3>Uruchomienie</h3>
<ol>
    <li>
    Na początku, w ramach oswojenia się ze środowiskiem wykonywaliśmy projekty próbne.
    Pierwszy z nich był praktycznie pusty, i miał za zadanie wyświetlić tylko i wyłącznie napis "uname". W tym celu, najpierw przeszliśmy do menu tworzenia nowych "itemów", czyli jednej z wielu opcji zawierających między innymi nowe projekty, foldery czy też pipeline'y, które to będą nas w szczególności interesowały w dalszej części zajęć.
    <img title="t" name="n" src="Screeny/Screenshot from 2023-04-30 22-08-27.png"/>
    Po wpisaniu odpowiedniej nazwy, wyświetlało nam się menu pozwalające na wybranie interesujących nas ustawień odnośnie konfiguracji i działania projektu. Nasz pierwszy projekt miał za zadanie tylko i wyłącznie wypisywać na ekran tekst, tak więc jedyną odpowiednią dla nas opcją było dodanie kolejnego "kroku" działania programu. Tam, mogliśmy wybrać czy chcemy wpisać jakąś komendę w shellu/bashu, podać odpowiedni plik wykonywalny itp. Dla nas wystarczająca była ta pierwsza opcja.
    <img title="t" name="n" src="Screeny/Screenshot from 2023-04-30 22-09-04.png"/>
    Po wybraniu tej opcji mogliśmy zapisać projekt, a następnie zakolejkować jego uruchomienie. W tym prostym przypadku ciężko było o jakieś problemy, więc po niedługim czasie zobaczyliśmy potwierdzenie sukcesu wykonania naszego projektu.
    <img title="t" name="n" src="Screeny/Screenshot from 2023-04-30 22-10-02.png"/>
    </li>
    <li>
    Po pierwszym oswojeniu się z działaniem Jenkinsa, mogliśmy podejść do ciut bardziej wymagającego problemu (choć nadal prostego). Tym razem pisaliśmy prosty skrypt mający na celu zwrócenie błędu w momencie, gdy podczas uruchamiania godzina jest nieparzysta. Kroki do jego wykonania były zbliżone do tych poprzednich, z tą różnicą że potrzebowaliśmy dodatkowego skryptu zapewniającego sprawdzenie godziny. Dodawaliśmy go w tym samym miejscu co wypisanie tekstu na ekran. Samego skryptu opisywać nie ma sensu, gdyż jest dość intuicyjny w swojej budowie.
    <img title="t" name="n" src="Screeny/Screenshot from 2023-05-01 10-28-06.png"/>
    Jak poprzednio, program działał bez większych problemów:
    <img title="t" name="n" src="Screeny/Screenshot from 2023-05-01 10-28-27.png"/>
    </li>
</ol>

<h3>Utworzenie "Prawdziwego" projektu</h3>
<ol>
    No i na tym etapie skończyły się rzeczy proste. Nadszedł czas aby zmierzyć się po raz kolejny z próbą pracy na projekcie (swoją drogą poleconym na samych zajęciach jako zdatnym do pracy), który już wcześniej sprawiał problemy podczas próby uruchomienia przez obrazy Dockera. Niezrażony poprzednimi doświadczeniami przystąpiłem do realizacji zadania. Pierwszym krokiem w drodze do realizacji tego celu było wrzucenie poprzednio utworzonych Dockerfilów do naszej gałęzi. Potem będziemy próbowali z poziomu Jenkinsa sklonować to repo, przejść do naszej gałęzi i zbudować odpowiednie obrazy. W idealnym świecie zakończyłoby się to pomyślnie zbudowanym projektem, aczkolwiek jak wszyscy dobrze wiemy ten świat nie jest idealny. Sukcesu nie wróżył dodatkowo fakt, że na poprzednich laboratoriach Dockerfile nie działały, i do tej pory nie udało mi się znaleźć przyczyny takiego stanu rzeczy, więc intuicja podpowiadała mi że uruchomienie projektu poprzez Jenkinsa może nie być wystarczającą pomocą w drodze do naprawy sytuacji. Nie oznaczało to jednak że nie zamierzam spróbować. Zgodnie z wolą Bożą utworzyłem nowy projekt Jenkinsa, który miał za zadanie wykonanie builda i testów naszego projektu. <br><br>
    Tym razem, poza napisaniem jakiegoś skryptu musieliśmy również podać repozytorium na którym chcemy pracować oraz jego konkretną gałęź, tak aby Jenkins wiedział na podstawie czego w ogóle pracujemy
    <img title="t" name="n" src="Screeny/Screenshot from 2023-05-01 10-54-35.png"/>
    Jako komendę, zamiast skryptu w shellu wpisujemy instrukcje budujące nasze dwa Dockerfile
    <img title="t" name="n" src="Screeny/Screenshot from 2023-05-01 10-54-44.png"/>
    <img title="t" name="n" src="Screeny/Screenshot from 2023-05-01 12-41-30.png"/>
    <img title="t" name="n" src="Screeny/Screenshot from 2023-05-01 12-41-55.png"/>
    Ku zaskoczeniu nikogo build poprzez Jenkinsa nadal nie działa. Jako plus można natomiast nadmienić że przynajmniej program jest przewidywalny, i niezależnie od próby zbudowania wywala się dokładnie w ten sam sposób, a wszystkie kroki poprzedzające uruchamianie testów wykonują się poprawnie, co uznaję za połowiczny sukces.
    
</ol>

<h3>Sprawozdanie (Wstęp)</h3>
<ol>
    <li>
    Z okazji pomyślnego zbudowania aplikacji byłem w stanie utworzyć na jego podstawie diagram UML prezentujący zarys (teoretycznego) działania uruchamiania aplikacji od momentu uruchomienia projektu z poziomu Jenkinsa do wyświetlenia się wyniku. Diagram ten będzie w przyszłości stanowił bazę, z którą będziemy mogli porównać proces budowania się tego projektu oraz wszystkich wykonanych w przyszłości (spojler: również teoretycznie).
    <img title="t" name="n" src="Screeny/Zrzut ekranu (40).png"/>
    Powyższy diagram aktywności zawiera podział na poszczególne etapy, przez które "przechodziliśmy" podczas uruchamiania projektu. Wzorując się na nim, będziemy mogli w przyszłości łatwiej zaprojektować i wdrożyć pipeline dla Jenkinsfile.
    </li>
    <li>
    Drugi diagram jest natomiast diagramem wdrożeniowym, przedstawiającym ogólną architekturę rozwiązania.
    <img title="t" name="n" src="Screeny/Zrzut ekranu (41).png"/>
    </li>

</ol>

<h3>Pipeline - Przygotowania</h3>
<ol>
    <li>
    Główna, i jednocześnie ostatnia część prac nad tym laboratorium polegała na napisaniu Jenkinsfile'a zawierającego części niezbędne do automatyzacji poprzedniego procesu, i uruchomienia całości za pomocą jednego pliku. Tego typu pliki składają się z przede wszystkim z:<br>
    - sekcji "agent", wskazującej w jakim miejscu poszczególne fragmenty bądź też cały pipeline zostaną wykonane w środowisku Jenkinsa<br>
    - parametrów, które są co prawda opcjonalne i da się bez nich uruchomić plik lecz dostarczają często istotnych informacji na temat aplikacji, takich jak credentialsy, zmienne konfiguracyjne, numery poszczególnych wersji programu itp.<br>
    - stage'y, czyli etapów które są niezbędne do poprawnego przeprowadzenia procesu budowania. Dla najprostszych Jenkinsfile'ów możemy wyróżnić trzy takie etapy: Build, Test oraz Deploy.
    </li>
    <li>
    Podstawowy zarys takiego pliku może wyglądać następująco:
    <div>
    pipeline {<br>
        &nbsp;&nbsp;agent any //wskazanie aby Jenkins wykonał kod w dowolnym dostępnym agencie<br>
        &nbsp;&nbsp;stages {<br>
            &nbsp;&nbsp;&nbsp;&nbsp;stage('Build') {<br>
                &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;steps {<br>
                    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;//kroki potrzebne do Buildu programu<br>
                &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}<br>
            &nbsp;&nbsp;&nbsp;&nbsp;}<br>
            &nbsp;&nbsp;&nbsp;&nbsp;stage('Test') {<br>
                &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;steps {<br>
                    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;//kroki potrzebne do Testu programu<br>
                &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}<br>
            &nbsp;&nbsp;&nbsp;&nbsp;}<br>
            &nbsp;&nbsp;&nbsp;&nbsp;stage('Deploy') {<br>
                &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;steps {<br>
                    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;//kroki potrzebne do Deployu programu<br>
                &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}<br>
            &nbsp;&nbsp;&nbsp;&nbsp;}<br>
        &nbsp;&nbsp;}<br>
    }<br>
    </div>
    </li>
    <li>
    Ponadto, oprócz pliku Jenkinsa, potrzebne są również:
    <ul>
        <li>Docker, w celu konteneryzacji procesu i poprawnej interpretacji Dockerfilów</li>
        <li>Jenkins, bo pracujemy w Jenkinsie to chyba oczywiste dość</li>
        <li>Git, czyli repozytorium z którego pobieramy wszystkie pliki oraz wprowadzamy zmiany celem zbudowania projektu</li>
    </ul>
    </li>
    <li>
    Kolejnym krokiem było zalogowanie się na konto na DockerHubie (bądź też jego utworzenie) i stworzenie tokenu, za pomocą którego później w Jenkinsfile'u będziemy mogli uzyskać dostęp do tego konta i umieścić na nim stworzone w pipelinie artefakty.
    <img title="t" name="n" src="Screeny/Screenshot from 2023-05-03 18-05-24.png"/>
    Token ten wykorzystujemy w Jenkinsie. W ustawieniach wchodzimy kolejno do: Dashboard -> Manage Jenkins -> Credentials -> Add domain, i tam podajemy między innymi token wygenerowany w DockerHubie jako password.
    <img title="t" name="n" src="Screeny/Screenshot from 2023-05-03 18-25-11.png"/>
    </li>
</ol>

<h3>Pipeline - Implementacja</h3>
<ol>
    <li>
    Najpierw tworzyliśmy nowy projekt Jenkinsa, w którym określaliśmy repozytorium z którego będziemy korzystać, konkretną gałęź, czyli każdy wybierał swoją indywidualną, oraz plik wykonywalny na podstawie którego będziemy przeprowadzać proces.
    <img title="t" name="n" src="Screeny/Screenshot from 2023-05-03 18-26-18.png"/>
    <img title="t" name="n" src="Screeny/Screenshot from 2023-05-03 18-26-45.png"/>
    Wykorzystywany plik Jenkinsa był od początku pisany wewnątrz repo, aby mieć pewność co do jego położenia w trakcie pracowania na nim.
    W moim przypadku składał się z 5 części: Prepare, Build, Test, Deploy i Publish, które po krótce opiszę w poniższych fragmentach.
    </li>
    <li>
        <ul>
            <li>
            Etapy przed stagem:
            <img title="t" name="n" src="Screeny/Zrzut ekranu (42).png"/>
            W tym fragmencie dzieją się dwie istotne rzeczy: po pierwsze wykorzystujemy credentiale z poprzedniego kroku jako zmienną DOCKERHUB_CREDENTIALS, dzięki czemu będziemy mogli się nią później posługiwać w celu uzyskania dostępu do konta, a po drugie definiujemy opcjonalny parametr uruchomienia programu. Nie jest w żaden sposób konieczny dla jego poprawnego działania i wklejony jest raczej w celu pokazania potencjalnej możliwości ustanowienia takiej zmiennej, wraz z jej wartością domyślną. Jeśli chcelibyśmy zrobić coś mającego większy wpływ na program nie byłby to zpory problem, gdyż możnaby na przykład zapisać zmienną określającą czy chcemy zapisać dodatkowe logi podczas przechodzenia przez pipeline'a, bądź też czy chcemy w ogóle uruchamiać testy na sklonowanym repo.
            </li>
            <li>
            Prepare:
            <img title="t" name="n" src="Screeny/Zrzut ekranu (43).png"/>
            W celu przygotowania pipeline'a usuwamy najpierw wszystkie pozostałości po poprzednich uruchomieniach komendą "rm...", a następnie clonujemy repo i tworzymy pliki dla przechowania logów, które bym miał gdyby wszystko działało prawidłowo
            </li>
            <li>
            Build:
            <img title="t" name="n" src="Screeny/Zrzut ekranu (44).png"/>
            W tej sekcji budujemy oraz uruchamiamy projekt, tak jak rzekomo powinienem robić według dokumentacji i jak działało podczas uruchamiania na maszynie wirtualnej. Zapisuję potencjalne logi powstałe na tym etapie i archiwizuję je instrukcją "archiveArtifacts"
            </li>
            <li>
            Test:
            <img title="t" name="n" src="Screeny/Zrzut ekranu (45).png"/>
            Wykonanie podobnych operacji celem wywołania testów jednostkowych, które powinny zadecydować o poprawności zbudowania się projektu w pipelinie.
            </li>
            <li>
            Deploy:
            <img title="t" name="n" src="Screeny/Zrzut ekranu (46).png"/>
            W tej sekcji usuwam niepotrzebne już kontenery z dockera, archiwizuję zebrane już logi oraz wyciągam pozostałe, jeśli takowe są jeszcze po uruchomieniu testów. Tego etapu nie miałem już możliwości przetestować więc pewnie są tam błędy i powinien zostać przeredagowany.
            </li>
            <li>
            Publish:
            <img title="t" name="n" src="Screeny/Zrzut ekranu (47).png"/>
            Na tym etapie teoretycznie powinno nastąpić zalogowanie się do konta na DockerHubie i wypchnięcie tam powstałych na poprzednich etapach artefaktów.
            </li>
        </ul>
    </li>
    <li>
    Tak utworzony plik w teorii powinien w rezultacie pozwolić na sprawne przeprowadzenie pipeline'a, ale w rzeczywistości otrzymywałem tylko błędy, i to na dość wczesnym etapie prac. Mimo usilnych starań nie byłem w stanie znaleźć żadnych informacji na temat pochodzenia ani potencjalnych przyczyn błędu, więc zmuszony jestem poddać się na tym etapie. Gdybym miał więcej czasu na wykonanie tego ćwiczenia najprawdopodobniej spróbowałbym rozpocząć całą pracę od zupełnie nowego projektu i na jego podstawie spróbował wykonać laboratoria, natomiast treść wyświetlanego błędu nie daje nawet jasnej informacji czy problem tym razem tkwi rzeczywiście w samym repozytorium na którym pracuje, czy też w jakimkolwiek innym miejscu pracy.
    <img title="t" name="n" src="Screeny/Screenshot from 2023-05-03 19-31-44.png"/>
    <img title="t" name="n" src="Screeny/Screenshot from 2023-05-03 19-32-17.png"/>
    </li>
</ol>

<h3>Wnioski</h3>

<ul>
    <li>
    Jenkins jest wszechstronnym narzędziem, które może zostać wykorzystane zarówno do automatyzacji i zapewnienia ciągłości działania drobnych aplikacji i skryptów, które dałoby się równie dobrze uruchomić jednorazowo za pomocą o wiele prostszych narzędzi, jak i większych projektów wymagających wielopoziomowej komunikacji pomiędzy wieloma komponentami, która byłaby bardzo kłopotliwa innymi środkami.
    </li>
    <li>
    Podczas pracy z bardziej zaawansowanymi pipeline'ami pomocne może okazać się wykonanie diagramu aktywności w UML. O ile forma takiego diagramu będzie się często zmieniała na skutek konfrontacji początkowych założeń z brutalną rzeczywistością, daje nam on dość dogłębny podgląd na pracę w poszczególnych etapach, a także pozwala lepiej uzmysłowić sobie cały proces.
    </li>
    <li>
    Jenkins jako aplikacja jest mało komunikatywny pod kątem wyświetlanych błędów, niezależnie od etapu na którym się one pojawiają, przez co wychwytywanie zarówno aktualnych jak i przyszłych pomyłek jest bardzo uciążliwe, przy czym nie pomaga również fakt dość małej ilości informacji w internecie, zwłaszcza w porównaniu z o wiele bardziej popularnymi narzędziami jak Git.
    </li>
    <li>
    Budowa Jenkinsfilów w teorii jest zrozumiała u podstaw i pozwalająca na utworzenie takowego pliku bez większych nakładów czasu, niestety jednak ich egzekucja jest o wiele trudniejszym zadaniem, i rzeczy które w teorii powinny działać z różnych przyczyn potrafią tutaj się wysypywać
    </li>
</ul>
