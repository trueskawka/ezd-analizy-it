GitHub
======

Proces komunikacji na GitHubie powinien zakładać jak największe zaufanie
i odpowiedzialność jej uczestników. Wpłynie to pozytywnie na ich
zaangażowanie, a w konsekwencji na cały proces komunikacji.

Publikujemy pod swoim nazwiskiem
--------------------------------

Każdy wkład do projektu powinien być publikowany na GitHubie przez osobę
go tworzącą (lub wiodącą w zespole osób tworzących). Decyzja o tym,
kiedy jest on gotowy do publikacji, powinna leżeć po stronie
publikującego i to on podejmuje decyzje o:

-  wewnętrznym procesie redakcyjnym w organizacji (np. upewnienie się,
   że tekst nie zawiera literówek, jest przystępny dla osób postronnych,
   w szczególności nietechnicznych)
-  weryfikacji zasadności wkładu i jego wartości dla projektu (tzw.
   sanity check)
-  zakresie i formie wkładu (niesprzecznej z wcześniejszymi ustaleniami,
   np. dokumenty publikowane są w formacie ``.rst``)

Narzucenie nadmiernego procesu weryfikacji wewnętrznej może negatywnie
wpłynąć na poczucie odpowiedzialności za wkład ("czy to rzeczywiście
coś, co chcę opublikować pod swoim nazwiskiem"), a w konsekwencji może
spowodować rozmycie odpowiedzialności w długim okresie.

W skrócie: szanujemy nawzajem swój wkład w projekt i zakładamy, że
publikowane są one zgodnie z najlepszą wiedzą publikującego.

Proponujemy rozwiązania
-----------------------

GitHub działa na zasadzie tzw. pull requestów, które są pewną propozycją
rozwiązania istniejącego problemu lub dodaniem nowej wartości do
projektu.

Issue
~~~~~

Na GitHubie narzędziem do śledzenia problemów i proponowanych usprawnień
w projekcie są issues. Dzięki możliwości zgłaszania ich przez każdą
osobę, która angażuje się w projekt open-source (m.in. deweloperów,
użytkowników), pozwala na usprawnianie komunikacji i rozmawianie o
priorytetach.

Dla zachowania pełnej historii komunikacji warto jest dodać do
repozytorium issue, które opisuje obszar problemowy i pozwala na
dyskutowanie o możliwych rozwiązaniach. Każdy issue można następnie
powiązać z konkretnym pull requestem, który go rozwiązuje.

Publikowanie pull requesta
~~~~~~~~~~~~~~~~~~~~~~~~~~

Aby móc opublikować pull requesta należy:

-  stworzyć forka repozytorium głównego na swoim koncie GH
-  zrobić ``git pull`` na swoim forku i dodać go jako ``remote`` do repozytorium
   lokalnego (zwyczajowo ``origin``)
-  dodać główne repozytorium projektu jako ``remote`` (zwyczajowo ``upstream``)
-  stworzyć brancha na proponowane rozwiązanie, dodawać na nim lokalnie
   zmiany
-  w momencie, kiedy zmiany są zadowalające dla publikującego, uporządkować
   ``git log``
-  poszczególne commity powinny być implementacją pełnych rozwiązań
   (pozwala to np. na wybieranie tylko części commitów z pull requesta
   [``cherrypicking``] i łatwe usunięcie niedziałającego rozwiązania w
   przypadku ewentualnych problemów)
-  zrobić ``git rebase`` proponowanych rozwiązań na najnowszą wersję
   master brancha na ``upstream``
-  to osoba proponująca rozwiązanie odpowiada za jego działanie i upewnienie
   się, że współgra z istniejącym kodem
-  zrobić ``git push`` na ``remote origin`` i opublikować pull reqesta do
   głównego repozytorium

Informacje w PR
^^^^^^^^^^^^^^^

Pull request powinien zawierać:

-  krótką nazwę opisującą istotę rozwiązania (np. 'Implementacja autoryzacji
   z OpenID'),
-  tag dotyczący obszaru problemowego (np. 'uprawnienia'),
-  informacje, jakie mogą być potrzebne osobie weryfikującej (np. 'To
   rozwiązanie zawiera bibliotekę X, możliwe do użycia są jeszcze biblioteki
   A i B, ale wybrane rozwiązanie ma ``<zalety>``. Dodatkowo, pytanie, czy nie
   powinniśmy lepiej przetestować ``<obszar>``.'),
-  [opcjonalnie] @-mention dla osób, do których osoba publikująca zwraca się
   o review (np. X zajmuje się obszarem uprawnień i na pewno chcę, żeby tu
   zajrzał),
-  [opcjonalnie] tag 'WIP' (work-in-progress) dla pull requestów, które nie
   implementują jeszcze w pełni rozwiązania, ale osoba publikująca chce o
   nim publicznie rozmawiać i zwrócić się o pomoc.

Rozmawiamy otwarcie
-------------------

Każdy pull request podlega ocenie osób uczestniczących w projekcie i
musi przejść proces weryfikacji. Osoba proponująca rozwiązanie nie
powinna być osobą jednocześnie je dodającą do projektu (w wyjątkowych
sytuacjach może być konieczne szybkie zmerge'owanie zmian, ale nie jest
to zalecana praktyka).

Zalety code review to przede wszystkim dyskutowanie zmian przed ich
wprowadzeniem (łatwiej jest coś zablokować, niż wyrzucić to z
repozytorium) oraz jasny, angażujący wszystkich uczestników proces
komunikacji.

Code review
~~~~~~~~~~~

Proces weryfikacji powinien angażować:

-  osobę publikującą,
-  osoby zajmujące się obszarem problemowym,
-  osobę zgłaszającą issue, jeśli pull request się do niego odnosi.

Każdy pull request powinien być zweryfikowany przez dwóch innych
członków zespołu i do jego zmerge'owania wystarczy większość głosów
uczestników.

W GitHubie w procesie review można:

-  komentować pull requesta ("mam pewne uwagi, ale nie chcę blokować, bo to
   tylko przecinki"),
-  zablokować pull requesta poprzez ``request changes`` ("mam uwagi krytyczne
   i nie chcę, żeby ktoś inny w zespole sprawdzał tego pull requesta, zanim
   ich nie naprawisz"),
-  zaakceptować poprzez ``approve`` ("uważam, że może to zostać zmerge'owane
   do repozytorium w obecnej formie").

Wprowadzanie zmian
~~~~~~~~~~~~~~~~~~

Osoba publikująca pull requesta powinna w trakcie komunikacji z zespołem
wprowadzać ustalane zmiany na swoim branch. W tym celu powinna:

-  zrobić ``interactive rebase`` w przypadku zmieniania istniejących commitów,
-  dodać commity, o ile potrzebne są dodatkowe rozwiązania,
-  zrobić ``git push origin +<nazwa_brancha>`` (force push) na swój remote
   fork, co zupdate'uje pull requesta na GitHubie.

Na GitHubie zostanie zachowana cała historia komunikacji.

Bad practices
-------------

-  Nie należy robić force pusha na master brancha, w szczególności w
   głównym repozytorium.
-  Nie należy tworzyć commitów, które naprawiają wcześniejsze commity, w
   tym samym pull requeście. Każdy commit w PR musi być samodzielnym
   rozwiązaniem, które przechodzi testy.
