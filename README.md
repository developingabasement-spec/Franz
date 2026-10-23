# Karteikasten – Vokabeltrainer

Vokabeltrainer mit Kapiteln, Unterkapiteln, Konjugation, Live-Sync (Supabase) und Lehrer-Sitzungen.

## Inhalt

| Datei | Wofür |
|---|---|
| `index.html` | Die komplette App |
| `supabase/01_vokabeln.sql` | Tabelle für die Vokabeln (Live-Sync) |
| `supabase/02_sitzungen.sql` | Lehrer-Modus und Sitzungen |
| `.github/workflows/supabase-wachhalten.yml` | Optional: hält Supabase wach |

## Einrichten

1. **Hochladen:** `index.html`, `README.md` und den Ordner `.github` in dein GitHub-Repository hochladen.
   **Den Ordner `supabase` NICHT hochladen** – darin steht der Generalcode im Klartext, und ein öffentliches Repository kann jeder lesen.
2. **GitHub Pages:** Settings → Pages → Branch `main`, Ordner `/ (root)` → Save.
3. **Supabase:**
   - SQL Editor: `01_vokabeln.sql` ausführen (falls noch nicht geschehen), dann `02_sitzungen.sql`.
   - Authentication → Sign In / Providers → „Allow anonymous sign-ins“ einschalten.
   - Authentication → URL Configuration → Site URL = deine GitHub-Pages-Adresse.
4. **App öffnen:** Unter „Live-Sync mit Supabase“ Project URL und anon public key eintragen
   (Supabase → Project Settings → API). Niemals den `service_role` key verwenden.
5. **Tipp:** Danach „Als HTML speichern“ mit Haken bei „Supabase-Verbindung mit einbauen“,
   die Datei in `index.html` umbenennen und auf GitHub ersetzen – dann muss niemand mehr etwas eintragen.

## Lehrer-Modus

- Startpasswort: `Franz` (in der App unter „Lehrer-Passwort ändern“ änderbar).
- Der Generalcode steht nur in `02_sitzungen.sql` (nur auf deinem PC aufbewahren!) und wird in Supabase verschlüsselt gespeichert – nicht in der App.

## Wachhalten (optional)

Repository → Settings → Secrets and variables → Actions → „New repository secret“:
- `SUPABASE_URL` = deine Project URL
- `SUPABASE_ANON_KEY` = dein anon public key

Danach pingt GitHub dein Supabase-Projekt alle 3 Tage an. Testen: Reiter „Actions“ → „Supabase wachhalten“ → „Run workflow“.

## Updates

Neue Version von `index.html` hochladen und die alte ersetzen. Die gespeicherten Vokabeln bleiben erhalten.
