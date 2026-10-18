# Auris

Portabler Musikplayer für Windows 11. Ordner kopieren, `Auris.exe` starten, keine Installation.

Auris ist für eine Person gebaut, die ihre Musik selbst verwaltet: lokale Dateien, Netzlaufwerke und Cloud-Ordner, dazu Playlists, die sich speichern, mitnehmen und mit anderen Playern austauschen lassen. Die Oberfläche folgt Windows 11, mit Glasfläche, aufgeräumten Bereichen und ohne verspieltes Beiwerk. Die Anregung kam von AIMP. Auris ist kein Skin und kein Nachbau, sondern ein eigener Player.

## Warum es das gibt

Viele Player sind entweder fest installiert, überladen oder an einen Dienst gebunden. Auris soll auf einem Rechner, einem zweiten Rechner oder einem USB-Stick gleich aussehen und dieselben Dateien abspielen. Die Daten bleiben neben dem Programm. Es gibt kein Konto und keine Pflicht, Musik in eine eigene Bibliothek zu importieren.

## Was der Player umfasst

Wiedergabe von MP3, FLAC, WAV, M4A, AAC, WMA, OGG und OPUS. Ausgabe über WaveOut, WASAPI, WASAPI Exclusive und ASIO. Lautstärke, Balance, Überblendung, ReplayGain, Suche im Titel und ein sichtbares Spektrum. Play, Pause, Stop, vor und zurück. Shuffle, Wiederholen und eine A-B-Schleife. Der nächste Titel startet von selbst. Fällt eine Datei auf einem Netzlaufwerk aus, wird der nächste erreichbare Titel genommen. Sind alle weg, stoppt die Wiedergabe und die Titel bleiben als offline markiert.

Mehrere Playlists, speicherbar in einem frei gewählten Ordner, lesbar und schreibbar als M3U und den üblichen Playlist-Dateien. Titel lassen sich einzeln oder mehrere auf einmal entfernen, sortieren, bewerten und per Ziehen umordnen. Die Spalten sind in der Breite verstellbar. Eine Warteschlange steht neben der Playlist: Stücke können als Nächstes oder später drankommen, ohne die gespeicherte Liste zu verändern. Zwischen Playlists blättern oder eine Liste bearbeiten unterbricht nicht, was gerade läuft. Erst ein bewusster Doppelklick oder Play startet dort etwas Neues. Dazu Schnellsuche, Bibliothek, Verlauf, Lesezeichen, Doppelte finden und Offline-Titel entfernen.

Ordner lassen sich im Player durchgehen, inklusive Laufwerken und eines eingetippten Netzwerkpfads wie `\\Server\Musik`. **Durchsuchen** öffnet den Windows-Dialog. Große Ordner auf Netzlaufwerken und in der Cloud sind vorgesehen. Was gerade nicht erreichbar ist, wird nicht abgespielt und bringt den Player nicht zum Stehen.

Internetradio über eine Stream-Adresse oder eine M3U- bzw. PLS-Datei. Sender lassen sich merken. Eine Suche nach Land und Name holt Stationen aus dem öffentlichen Radioverzeichnis.

Equalizer mit zehn Bändern, festen Vorlagen wie Classic, Pop, Rock und Vocal, plus eigenen Vorlagen, die bleiben. Songtext aus der Datei oder von lrclib.net, in einem Seitenbereich, mit einer ruhigen Markierung der aktuellen Zeile.

Darstellung über dunkles Glas, dunkles Acryl oder helles Glas, dazu eine Akzentfarbe. Weitere Farben kommen als JSON-Datei in den Ordner `Skins`. Die linke Leiste lässt sich auf die Symbole einklappen. Ein Mini-Player bleibt über den anderen Fenstern. Die Titelleiste folgt dem Farbschema von Windows, einschließlich der Akzentfarbe, wenn Windows sie für Titelleisten verwendet. Fenstergröße und Spaltenbreiten werden gemerkt. Schließen kann ins Tray gehen. Ein Schlaf-Timer beendet die Wiedergabe nach einer gesetzten Zeit.

Beim ersten Start wird die Sprache abgefragt: Deutsch, Englisch, Japanisch oder vereinfachtes Chinesisch. Dieselbe Wahl steht danach in den Einstellungen. Der laufende Titel erscheint in der Windows-Now-Playing-Ansicht und im Lautstärken-Fliegfenster; die Media-Tasten der Tastatur steuern die Wiedergabe.

## Grenzen

Auris ist ein Player für eine Person an einem Windows-11-Rechner mit 64 Bit. Zwei Personen bearbeiten nicht gleichzeitig dieselbe Playlist. Der Player ersetzt keinen Streaming-Dienst und bringt keine eigene Cloud mit. Was offline ist, kann er nicht herbeizaubern. Er liest die Dateien dort, wo sie liegen.

## Portabel nutzen

Der veröffentlichte Ordner ist das ganze Programm. Diesen Ordner kopieren, nicht nur die EXE. Einstellungen, Sitzung, Cover und Plugin-Notizen liegen daneben in `data`. Skins liegen in `Skins`. Eine eigene Erweiterung kommt als DLL in `Plugins`.

Veröffentlichen, im Ordner der `Auris.csproj`:

```bat
dotnet publish Auris.csproj -c Release -r win-x64 --self-contained true
```

Die fertige Fassung liegt in `bin\Release\net9.0-windows10.0.22621.0\win-x64\publish\`.

## Bauen

Visual Studio 2022 oder neuer, Workload **Windows-Anwendungsentwicklung**, .NET 9. `Auris.sln` öffnen, Startprofil **Unpackaged**. Oben **Release** und **x64** wählen, wenn eine weitergebbare Fassung entstehen soll. **Erstellen** allein erzeugt nur die Fassung zum Testen.

## Erweitern

Die Darstellung lässt sich über die eingebauten Flächen oder eine JSON-Datei im Ordner `Skins` ändern. Eine Erweiterung implementiert `Auris.IPlayerPlugin` im Projekt `PluginApi`. Das mitgelieferte `PluginBeispiel` schreibt nach `data/plugin-log.txt`. Ereignisse sind Titel, Play, Pause und Stop. Befehle sind Play, Pause, Stop, Weiter und Anhängen.

## Lizenz

Open Source und frei nutzbar, auch kommerziell. Die Lizenz ist MIT: Auris darf verwendet, weitergegeben und verändert werden. Die genauen Bedingungen stehen in der Datei LICENSE im Projektordner.

---

# Auris

A portable music player for Windows 11. Copy the folder, start `Auris.exe`, no installation.

Auris is built for one person who keeps their own music: local files, network drives and cloud folders, plus playlists that can be saved, carried along and exchanged with other players. The interface follows Windows 11, with a glass surface, calm areas and nothing playful. The idea came from AIMP. Auris is not a skin and not a copy. It is its own player.

## Why it exists

Many players are either tied to an installer, overloaded, or bound to a service. Auris should look the same and play the same files on one computer, a second computer or a USB stick. The data stays next to the program. There is no account and no need to import music into a private library.

## What the player covers

Playback of MP3, FLAC, WAV, M4A, AAC, WMA, OGG and OPUS. Output through WaveOut, WASAPI, WASAPI Exclusive and ASIO. Volume, balance, crossfade, ReplayGain, search within the track and a visible spectrum. Play, pause, stop, previous and next. Shuffle, repeat and an A-B loop. The next track starts on its own. If a file on a network drive drops out, the next reachable track is used. If none remain, playback stops and the tracks stay marked as offline.

Several playlists, saved to any folder you choose, readable and writable as M3U and the usual playlist files. Tracks can be removed one by one or several at once, sorted, rated and reordered by dragging. The columns can be resized. A queue sits beside the playlist: tracks can play next or later without changing the saved list. Browsing or editing playlists does not interrupt what is playing. Only a deliberate double-click or Play starts something new there. Also included: quick search, library, history, bookmarks, finding duplicates and removing offline tracks.

Folders can be browsed in the player, including drives and a typed network path such as `\\Server\Music`. **Browse** opens the Windows dialog. Large folders on network drives and in the cloud are expected. What is not reachable is not played, and it does not freeze the player.

Internet radio from a stream address or an M3U or PLS file. Stations can be saved. A search by country and name fetches stations from the public radio directory.

An equalizer with ten bands, built-in presets such as Classic, Pop, Rock and Vocal, plus your own presets, which are kept. Lyrics from the file or from lrclib.net, in a side panel, with a quiet highlight on the current line.

Appearance through dark glass, dark acrylic or light glass, plus an accent color. Further colors go in as a JSON file in the `Skins` folder. The left bar can collapse to icons. A mini player stays above other windows. The title bar follows the Windows color scheme, including the accent color when Windows uses it for title bars. Window size and column widths are remembered. Closing can go to the tray. A sleep timer ends playback after a set time.

On the first start the language is asked: German, English, Japanese or Simplified Chinese. The same choice stays in Settings afterwards. The current track appears in the Windows Now Playing view and in the volume flyout; the keyboard media keys control playback.

## Limits

Auris is a player for one person on one 64-bit Windows 11 computer. Two people do not edit the same playlist at the same time. The player does not replace a streaming service and does not bring its own cloud. What is offline cannot be fetched out of nothing. It reads the files where they are.

## Portable use

The published folder is the whole program. Copy that folder, not only the EXE. Settings, the session, covers and plugin notes sit beside it in `data`. Skins sit in `Skins`. Your own extension goes in as a DLL in `Plugins`.

Publish from the folder that contains `Auris.csproj`:

```bat
dotnet publish Auris.csproj -c Release -r win-x64 --self-contained true
```

The finished build is in `bin\Release\net9.0-windows10.0.22621.0\win-x64\publish\`.

## Building

Visual Studio 2022 or newer, workload **Windows application development**, .NET 9. Open `Auris.sln`, start profile **Unpackaged**. Choose **Release** and **x64** at the top when you want a build you can hand on. **Build** alone only produces the version used for testing.

## Extending

The look can be changed with the built-in surfaces or a JSON file in the `Skins` folder. An extension implements `Auris.IPlayerPlugin` in the `PluginApi` project. The included `PluginBeispiel` writes to `data/plugin-log.txt`. Events are track, play, pause and stop. Commands are play, pause, stop, next and append.

## License

Open source and free to use, including commercially. The license is MIT: Auris may be used, shared and changed. The exact terms are in the LICENSE file in the project folder.

