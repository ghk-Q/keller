# Kellerlager-Demo als App auf dem iPad

Diese App läuft vollständig auf dem iPad:
- keine Anmeldung, kein Server, keine Benutzer
- alle Daten bleiben auf dem Gerät
- startet nach der Einrichtung auch ohne Internet
- Live-Kamera-Scan funktioniert

## Warum ein einmaliger Upload nötig ist

Das iPad kann HTML-Dateien aus der Dateien-App nicht als App starten. Die Vorschau dort führt keine Programme aus. Die App muss deshalb **einmal** von einer `https://`-Adresse geladen werden. Danach liegt sie als Symbol auf dem Home-Bildschirm und läuft offline. Die Daten werden **nicht** an diese Adresse übertragen, sie bleiben nur auf dem iPad.

## Einrichtung (ca. 10 Minuten, einmalig)

1. **Ordner hochladen.** Den Ordner `ipad-app` (alle 8 Dateien) auf einen Webspace mit HTTPS laden. Möglichkeiten:
   - der Webspace eurer Praxis-Homepage, z. B. Unterordner `/lager-demo/`
   - kostenlos mit Konto: **Netlify** (app.netlify.com → „Deploy manually“, Ordner hineinziehen), **Cloudflare Pages** oder **GitHub Pages**
2. **Am iPad in Safari** die Adresse öffnen, z. B. `https://eure-praxis.at/lager-demo/`.
3. **Teilen-Symbol → „Zum Home-Bildschirm“ → Hinzufügen.**
4. Die App ab jetzt **nur noch über das Symbol** starten. Sie öffnet sich ohne Browserleiste und funktioniert auch ohne Internet.
5. Beim ersten Scan die Kamera **erlauben**.

## Gut zu wissen

- **Daten gehören zum Home-Bildschirm-Symbol.** Was in Safari selbst eingegeben wurde, sieht die App am Home-Bildschirm nicht (und umgekehrt). Wird das Symbol gelöscht, sind die Daten weg.
- **Sicherung:** „Mehr → Datensicherung speichern“ legt eine Datei in der Dateien-App ab. Mit „Datensicherung einspielen“ kommt alles zurück, auch auf einem anderen iPad.
- **Mehrere Geräte** teilen in der Demo **keine** Daten. Jedes iPad hat sein eigenes Lager. Gemeinsame Daten gibt es in der Server-Version (PocketBase).
- **Lieferschein-Erkennung** gibt es in der Offline-Demo nicht.
- **Test-Barcodes:** „Mehr → Test-Barcodes anzeigen“ auf einem zweiten Gerät öffnen oder ausdrucken.
- **Update:** neue Dateien auf den Webspace laden, dann die App einmal mit Internet öffnen. Die Daten bleiben erhalten.

## Ohne Webspace, nur zum kurzen Ausprobieren

Auf einem PC oder Mac im selben WLAN im Ordner `ipad-app` ausführen:

```
python3 -m http.server 8000
```

Am iPad `http://<IP-des-PCs>:8000` öffnen. Das läuft, aber über `http` erlaubt Safari keine Live-Kamera (Scan per Foto geht) und die App startet nicht offline.
