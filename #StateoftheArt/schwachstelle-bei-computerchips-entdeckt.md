# Schwachstelle bei Computerchips entdeckt

_Captured: 2019-05-28 at 12:01 from [www.ingenieur.de](https://www.ingenieur.de/technik/fachbereiche/ittk/schwachstelle-bei-computerchips-entdeckt/?utm_source=Maileon&utm_medium=email&utm_campaign=NewsletterING&utm_content=20190528)_

FPGA-Chips gelten als die Legosteine der Computerhersteller und bislang hielt man sie fur relativ sicher. Forscher des Karlsruher Instituts fur Technologie (KIT) fanden nun eine Schwachstelle.

![FPGA-Chips](https://www.ingenieur.de/wp-content/uploads/2019/05/2019_068_Schwachstelle-von-Clouddienst-Hardware-aufgedeckt-e1558529107192.jpg)

> _Field-Programmable Gate Arrays (FPGAs) sind flexibel und vielseitig einsetzbar. Das haben sie den spezialisierten Chips voraus. Bislang galten sie auch als besonders sicher. Das widerlegte nun ein Forscherteam vom KIT._

Die FPGA-Chips sind die aktuellen digitalen Tausendsassas der Computerbranche, verbrauchen sie doch vergleichsweise wenig Strom. Damit fallt die Wahl meist auf sie, wenn es um Anwendungen in großen Rechenzentren fur Clouddienste geht. Diese kleinen programmierbaren Chips haben zudem noch 2 weitere entscheidende und praktische Vorzuge: Sie konnen nahezu alle Funktionen anderer Chips ubernehmen, sind also nicht auf eine einzige Aufgabe zugeschnitten. Das macht sie im Vergleich zu gewohnlichen spezialisierten Chips so flexibel. Und deshalb nutzt man sie auch meist bei der Entwicklung neuer Gerate und Systeme. „FPGAs werden zum Beispiel in der ersten Produktcharge neuer Gerate verbaut, weil man sie im Gegensatz zum Spezialchip, dessen teure Entwicklung sich nur bei sehr großen Stuckzahlen lohnt, nachtraglich noch verandern kann", sagt Dennis Gnad vom Institut fur Technische Informatik (ITEC) des KIT.

Der 2. Vorteil: Die FPGA-Chips konnen beliebig aufgeteilt werden. Das bedeutet, 2 Kunden konnen sich praktisch einen einzigen Chip teilen. Der eine nutzt dabei einfach die obere Halfte des Chips, der andere die untere Halfte. Das ist besonders fur Cloudanbieter interessant, wenn diese ihre Dienste vermarkten wollen. Gute und damit verbreitete Einsatzgebiete der FPGA-Chips sind zum Beispiel Anwendungen mit Datenbanken, mit Kunstlicher Intelligenz, Maschinelles Lernen und auch Finanzapplikationen. Außerdem werden die Chips in Smartphones eingesetzt, fur Netzwerke, in der Medizintechnik, Fahrzeugelektronik sowie in der Luft- und Raumfahrt.

## FPGA-Chips bieten Schwachstellen fur Hacker

In verschiedenen Tests deckten Forscher des KIT nun allerdings potenzielle Lucken in FPGA-Chips auf. Cyberkriminelle konnten sie nutzen, um diese Chips und die damit verbundenen Systeme anzugreifen, zu manipulieren oder gar zu zerstoren. Das Problem liegt dabei genau in der Verwendung der FPGA-Chips durch mehrere Nutzer zur gleichen Zeit. Ideenreichen Hackern bietet gerade die Vielseitigkeit und Flexibilitat der Chips die Moglichkeit, mit sogenannten Seitenkanal-Attacken Zugriff auf die Chips zu erlangen. Seitenkanalangriffe nutzen Schwachstellen im Einbau und in der Umsetzung von bestimmten Methoden, Verfahren, Protokollen, Betriebssystem, Hardware oder einem Algorithmus aus.

Dabei ist der Algorithmus selbst allerdings nicht das erklarte Ziel des Angriffs. Diese Attacke entsteht in der Regel uber die Beobachtung des Systems. Hacker verschaffen sich beispielsweise Zugang zum Energieverbrauch des Chips. Dieser verrat ihnen Informationen, mit denen sie in der Lage sind, seine Verschlusselungen zu durchbrechen. Neben dem Energieverbrauch konnen auch elektromagnetische Abstrahlung oder der Zeitverbrauch einer Operation Informationen preisgeben, die Hacker fur ihre Angriffe ausnutzen.

## Die Losung konnte im unmittelbaren Zugriff liegen

Die Forscher warnen: Gerade chip-interne Messungen bieten die Moglichkeit, dass ein Kunde des Clouddienstes einen anderen ausspionieren kann. Hacker sind daruber hinaus in der Lage, Schwankungen des Energieverbrauchs nicht nur auszuspahen, sondern sie sogar selbst zu erzeugen. Das konnte die Berechnungen anderer Kunden verfalschen oder sogar den gesamten Chip zum Absturz bringen, erklaren die Forscher. Diese Gefahren beschranken sich nach Ansicht der Wissenschaftler nicht nur auf die FPGA-Chips, sondern tauchen durchaus auch bei anderen Chips auf. Es betrifft zum Beispiel solche, die haufig fur Anwendungen im Internet der Dinge eingesetzt werden. Das konnen unter anderem intelligente Heizungssteuerungen oder Beleuchtungen sein - also durchaus ganz alltagliche Anwendungsbereiche.

Nach der Entdeckung dieser Schwachstelle widmen sich die Forscher der Losung des Problems. Ihr Ansatz: Sie wollen den unmittelbaren Zugriff der Nutzer auf die FPGA-Chips beschranken. „Die Schwierigkeit dabei liegt darin, bosartige Nutzer herauszufiltern, ohne gutwillige Verwender zu sehr einzuschranken", erklart Dennis Gnad vom KIT.

**Weitere IT-Themen:**
