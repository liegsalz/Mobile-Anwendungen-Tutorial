# Von Hello World bis zum Play Store!

## Inhaltsverzeichnis

**Android - Google Play Store:**

0. App programmieren
1. Setup mit EAS
   1. Login
   2. Init
2. Release bauen
3. Store Eintrag
4. Tester hinzufügen

**Expo EAS (iOS & Android):**

0. App programmieren
1. Setup mit EAS
   1. Login
   2. Init
2. Branch publishen
3. Freund:innen einladen

# Android - Google Play Store

## Step 0: App programmieren

Erstelle deine neue App mit

```bash
$ npx create-expo-app -t expo-template-blank-typescript
```

und füge dein Code hinzu!

```typescript
export const App = () => (
  <View>
    <Text>Hello MUC.DAI</Text>
  </View>
);
```

## Step 1: Setup mit EAS

### Step 1.1: Login

du musst, um deine App zu bauen, dein Projekt mit deinem Expo Account verknüpfen:

```bash
$ eas login
```

Im Terminal wirst du aufgefordert, die Daten für deinen Expo-Account einzugeben.

### Step 1.2: Init

Um die erforderlichen Konfigurationsdateien zu hinterlegen, musst du den folgenden Befehl ausführen:

```bash
$ eas init
```

du kannst selbst entscheiden, ob du ein neues Projekt erstellen möchtest oder es einem bestehenden hinzufügen möchtest. Normalerweise erstellt man jedoch ein neues Projekt.

## Step 2: Release bauen

Mit:

```bash
$ eas build -p android
```

kannst du ein Android App Bundle erstellen. Dieses ist ähnlich wie eine APK, jedoch speziell für den Google Play Store vorgesehen.

Beim ersten Ausführen werden Dir folgende Fragen gestellt:

- What would you like your Android application id to be?

  > In der Android [Dokumentation](https://developer.android.com/build/configure-app-module) stehen alle Infos die du zur App ID brauchst. Beispiel: edu.hm.liegsalz.hellomucdai.

- Generate a new Android keystore?
  > Auch hierzu mehr in der [Dokumentation](https://developer.android.com/training/articles/keystore). Im Zweifelsfall "Yes" wählen.

Sobald der Build Prozess fertig ist, kann man das .aab-File herunterladen. Den Link findet man im Terminal:

![Build link](/step4_1.png)

## Step 3: Store Eintrag erstellen

In der [Play Store Developer Console](https://play.google.com/console) muss man, nach einem erfolgreichen Login, folgende Schritte ausführen:

1. Oben rechts auf App Erstellen.
2. Informationen Ausfüllen und Erklärungen akzeptieren. Danach, rechts unten auf App erstellen.
3. In der Navigationsleiste Rechts auf Test > Interner Test.
4. Oben rechts auf Neuen Release erstellen.
5. Das .aab-File von Schritt 2 hier hochladen und restliche Informationen ausfüllen.

   - Release-Name: Nur für Entwickler sichtbar. Am besten etwas eindeutiges, womit man Releases unterscheiden kann.
   - Versionshinweise: Wird als Changelog dann im Store angezeigt, könnte so aussehen:

     ```xml
     <en-US> The new version adds a new language! </en-US>
     <de-DE> Die neue Version fügt eine neue Sprache hinzu! </de-DE>
     <es-ES> ¡La nueva version añade un nuevo idioma! </es-ES>
     ```

6. Rechts unten auf Weiter und dann wieder auf "Speichern".

## Step 4: Tester hinzufügen

Unter Tester kannst du nun deine Freund:innen einladen! Erstelle dafür am besten eine neue E-Mail-Liste.

Wichtig: es müssen die Emails sein, mit denen deine Freund:innen im Google Play Store eingeloggt sind.

# Android & iOS - EAS und Expo

## Step 0: App programmieren

Erstelle deine neue App mit

```bash
$ npx create-expo-app -t expo-template-blank-typescript
```

und füge dein Code hinzu!

```typescript
export const App = () => (
  <View>
    <Text>Hello MUC.DAI</Text>
  </View>
);
```

## Step 1: Setup mit EAS

### Step 1.1: Login

du musst, um deine App zu bauen, dein Projekt mit deinem Expo Account verknüpfen:

```bash
$ eas login
```

Im Terminal wirst du aufgefordert, die Daten für deinen Expo-Account einzugeben.

### Step 1.2: Init

Um die erforderlichen Konfigurationsdateien zu hinterlegen, musst du den folgenden Befehl ausführen:

```bash
$ eas init
```

du kannst selbst entscheiden, ob du ein neues Projekt erstellen möchtest oder es einem bestehenden hinzufügen möchtest. Normalerweise erstellt man jedoch ein neues Projekt. Falls du planst, dein Projekt zu teilen, solltest du, wie unter Schritt 3 beschrieben, eine neue Organisation erstellen.

## Step 2: Branch publishen

Ähnlich wie bei Git, kannst du deine App in verschiedene Branches releasen:

```bash
$ eas update --branch=branch-name --message=update-message
```

Wenn wir. zum Beispiel, das neue Feature XYZ in den Main-Branch _updaten_ wollen:

```bash
$ eas update --branch=main --message="Implemented feature XYZ"
```

## Step 3: Freund:innen einladen

Im [Expo Dashboard](https://expo.dev) findest du in der rechten Menüleiste all deine Projekte.

Falls du für dein Projekt keine Organisation angelegt hast (was nicht zwingend notwendig ist), kannst du deine Freund:innen zu deiner Organisation, mit all deinen privaten Projekten, unter `Settings > Members` hinzufügen.

Falls du lieber nur ein oder bestimmte Projekte mit deinen Freund:innen teilen möchtest, solltest du am besten eine Organisation erstellen. Dafür clicke oben auf deinen `Account-Namen > Create Organization`, Information ausfüllen und führe dann `eas init` aus, um die Organisation auszuwählen.
