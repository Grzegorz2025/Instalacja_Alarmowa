## **Instalacja alarmowa**

Grzegorz Górniak <br>
grzesgorniak@student.agh.edu.pl

## **Opis Modelu**

Model instalacji alarmowej dotyczy systemu alarmowego budynku mieszkalnego z systemem informacji o wykryciu zdarzenia (włamanie/ wtargnięcie). System po wykryciu zdarzenia z jednego z czujników uruchamia zapis wideo (od momentu wykrycia zdarzenia), alarm (ostrzeżenia świetlne i dźwiękowe) oraz jest w stanie powiadomić służby. System zbiera wszystkie informacje z czujników i podejmuje decyzję, aby uruchomić alarm, włączyć kamery oraz np. w odpowiednim momencie sterować mechanizmem zamykania wybranych drzwi tak aby: uchronić kluczowe pomieszczenia przed wtargnięciem, zatrzasnąć potencjalnego intruza do czasu przyjazdu policji. System otrzymuje również informacje z czujników, aby wysłać sygnał do kamery, która rozpoczyna zapis rejestrowanego obrazu wstecz do godziny czasu z różnych kamer w budynku. System informowania służb wysyła telefoniczne powiadomienie do jednostki okolicznej policji, gdy w budynku jest wykryte zdarzenie o wtargnięciu i sygnał taki nie zostanie zdezaktywowany w odpowiednim czasie (prewencja przypadkowego uruchomienia alarmu przez czynniki niezależne). System ten jest niezależny od głównego, ale współpracujący w celu ochrony przed potencjalnym atakiem, dlatego zawiera dwie pamięci oraz osobny procesor, który w sposób indywidualny przetwarza dane z czujników na innych zasadach niż system główny. Jedna z pamięci takiego procesu jest zastosowana do zbierania i przechowywania nagrań dla służb mundurowych w celu ułatwienia śledztwa po wtargnięciu.

### **SPIS KOMPONENTÓW**

## **URZĄDZENIA:**
1. "this_MotionSensor" - czujnik ruchu, umieszczony w korytarzu pomieszczenia
2. "this_MagneticAlarmSensor" - kontaktron, umieszczony we framudze drzwi, w celu wykrycia ich otwarcia
3. "this_Camera" - kamera, umieszczona przed budynkiem, obejmując zasięgiem wejście do niego
4. "this_LaserSensor" - czujnik laserowy, umieszczony przed budynkiem, wykrywa wtargnięcie na podjazd
5. "this_AlarmUnit" - jednostka alarmowa, moduł alarmowy wyzwalający ostrzeżenia świetlne i dźwiękowe o wykryciu zdarzenia
6. "this_DoorLockMechanism" - mechanizm blokujący drzwi, dodatkowa blokada (oprócz zamka) zamykająca drzwi
7. "this_Phone" - moduł telefonu, służący do poinformowania policji o wtargnięciu

## **PROCESORY:**

1. procesor główny, którego zadaniem jest sterowaniem całym systemem czujników oraz urządzeń w taki sposób, aby ostrzegać i informować o potencjalnym zdarzeniu takim jak włamanie na teren posesji
2.	procesor pomocniczy, którego zadaniem jest odpowiednia interpretacja danych z czujników, aby podjąć decyzję o zawiadomieniu organów o popełnieniu przestępstwa

## **PROCESY:**
1. proces główny, który ubsługuje kamerę, czujnik wykrycia ruchu, czujnik wykrycia otwarcia drzwi, czujnik laserowy oraz zapis nagrań video
2. proces pomocniczy, który obsługuje powyższe funkcje z tym, że analizuje te wątki i umożliwia zadzwonienie na policję.

## **PAMIĘCI ŚŁUŻACE DO POPRAWNEGO DZIAŁANIA PROCESÓW:**

1.	RAM
2.	Flash
3.	Pamięć, na którą zgrywane są dane z rejestracji video w postaci plików

## **WĄTKI:**

**A) wątki służące do detekcji zdarzenia:**
1.	Motion Detected, po wykryciu ruchu przesyła informację do kontrolerów
2.	Magnet Alarm, po wykryciu otwarcia drzwi lub okien przesyła informację do kontrolerów
3.	Laser Alarm, po wykryciu wejścia na podjazd budynku lub innych kluczowych wejść na zewnętrzne tereny posesji przesyła informację do kontrolerów
4.	Camera Check Detection, detekcja zdarzenia takiego jak wykrycie osoby przez kamerę

**B) wątki służące do interpretacji danych z czujników oraz podejmowania odpowiednich decyzji:**

1.	Control Rules, otrzymuje informacje z wszystkich czujników, wyzwala alarmy, uruchamia zapis wideo
2.	Process Video, przetwarzanie pliku wideo z kamery
3.	Video Recording, zapis pliku wideo w przypadku wykrycia zdarzenia i rozpoczęcia zapisu
4.	Alarm ON, uruchomienie jednostki alarmowej wyzwalającej ostrzeżenia o wtargnięciu. Również stosowane są odpowiednie zabezpieczenia takie jak blokowanie drzwi systemem lock door czy uruchomienie dźwiękowego ostrzeżenia na terenie posesji.
5.	Call Police Rules, informacja policji (telefoniczna) o wtargnięciu - po wykryciu zdarzenia

## **SYSTEM:**

1.	Security System - główny system opisujący działanie infrastruktury zabezpieczającej

## **KONTROLERY:**
1.	kontroler główny
2.	kontroler dodatkowy wzywający policję

## **POŁĄCZENIA:**
1.	połączenie magistralą Ethernet Communication

## **TYP DANYCH ZAPISU WIDEO:**

1.	zapis danych video w formie pliku mp4

## **Podstawowe analizy systemu:**

| Analiza   | Wynik     |
|-----------|-----------|
| ARINC429 Consistency   | pozytywna |
| Port Connenction       | pozytywna |
| Binding Contraints     | pozytywna |

## **Analiza zapotrzebowania na moc**
<img width="350" height="621" alt="analiza_moc" src="https://github.com/user-attachments/assets/6332e42b-3f5c-416b-b660-1bb3e4fb7b58" />

## **Analiza wagowa**
<img width="818" height="603" alt="analiza_masa" src="https://github.com/user-attachments/assets/05465874-47d6-43c1-af8f-300bdb71dd39" />

### **Model projektu**
<img width="2324" height="961" alt="Instalacja_alarmowa" src="https://github.com/user-attachments/assets/ae9b3001-8f17-4c62-ba62-33a1ae8f277b" />

## **Literatura**

[1] OSATE 2 - Open Source AADL Tool Environment - https://osate.org/ <br>
[2] AADL Community Resources and Examples - https://github.com/osate <br
[3] SAE International, "AS5506C: Architecture Analysis & Design Language (AADL)," SAE International Standard, 2017 - https://www.sae.org/standards/content/as5506c/>
