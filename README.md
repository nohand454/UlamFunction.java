// Die Hauptklasse des Programms – muss mit dem Dateinamen übereinstimmen (UlamFunction.java)
public class UlamFunction {
// Die main-Methode – Einstiegspunkt des Programms
    public static void main(String[] args) {
        final int LIMIT = 1_000_000; // Grenze bis wohin überprüft wird (alle Zahlen < 1 Mio)
        boolean allReachOne = true;  // Variable, um zu speichern, ob alle Zahlen bei 1 enden
// Schleife über alle Zahlen von 1 bis LIMIT - 1
        for (int i = 1; i < LIMIT; i++) {
            // Prüfe, ob die aktuelle Zahl bei 1 endet
            if (!reachesOne(i)) {
                // Falls nicht, gib sie aus und breche die Schleife ab
                System.out.println("Number " + i + " did NOT reach 1!");
                allReachOne = false; // setze das Flag auf false
                break; // Schleife abbrechen – wir haben eine Zahl gefunden, die nicht endet
            }
        }
    // Nach der Schleife: wenn alle Zahlen korrekt waren
        if (allReachOne) {
            System.out.println("All numbers < 1,000,000 reach 1."); // Erfolgsnachricht
        } else {
            System.out.println(" Some number did not reach 1."); // Fehlernachricht (sollte nie erscheinen)
        }
    }
// Methode, die prüft, ob eine Zahl n durch die Ulam-Folge bei 1 endet
    public static boolean reachesOne(long n) {
        // Solange n nicht 1 ist, wende die Regeln der Ulam-Funktion an
        while (n != 1) {
            if (n % 2 == 0) {
                n = n / 2; // Wenn n gerade ist: teile durch 2
            } else {
                n = 3 * n + 1; // Wenn n ungerade ist: n = 3n + 1
            }
        }
        // Wenn wir aus der Schleife rauskommen, ist n == 1, also true zurückgeben
        return true;
    }
}
