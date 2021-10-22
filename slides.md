# Angular Kompakt

Willkommen bei Ihrer Angular Schulung!

---

# Setup der Development-Umgebung

1. Node.js
2. Node Paket Manager
3. Angular CLI
4. Guter Editor / IDE
5. Git
6. Terminal


---

# Setup: Node.js

Homepage: https://nodejs.org

Installation entweder über den Standard-Installer [^1] (unter Windows) bzw. über Paketmanger des Betriebssystems.

Für Schulungen bevorzuge ich die LTS-Version (Long Term Support). Zumal aktuell die Current-Version von der Angular CLI offiziell (noch) nicht unterstützt wird.

Alternativ kann die Installation über einen Node-Versionsmanager gemacht werden - insbesondere, wenn man mehrere Node-Versionen unterstützen muss.

[^1]: Bei der Installation über den Installer unter Windows bitte den Haken bei der nativen Tool-Unterstützung nicht(!) setzen.

---

# Setup:  Node Paket Manager

Alternativen:

- npm
- yarn
- pnpm

Bei der Windows-Installation kommt normalerweise der Standard-Paketmanager  ```npm``` mit. Für die Schulung bleibe ich auch bei diesem.

---

# Setup: Angular CLI

Die Angular CLI ist ein Kommandozeilen-Tool, dass wir benutzen

-  beim Projektstart
- während der Entwicklungszeit
  - als lokaler Server
  - zum Starten der Testumgebung
- zum Erstellen neuer Code-Bausteine
- zum Erstellen eines optimierten Produktions-Build

Während die globale Installation des Tools nicht zwingend notwendig ist, vereinfacht es jedoch den täglichen Gebrauch im Terminal:

```bash
npm install --global @angular/cli
```

---

# Setup: Guter Editor/IDE

Prinzipiell ist jeder Texteditor ausreichend. Empfohlen sind natürlich Editoren bzw. Integrierte Entwicklungsumgebungen, die sich durch eine gute Unterstützung für JavaScript/TypeScript, CSS und schlussendlich HTML auszeichnen.

Idealerweise unterstützt der Editor zusätzlich Angular-Features wie zum Beispiel die Template-Syntax direkt oder über nachinstallierte Plugins.

Empfehlungen:
- [Visual Studio Code](https://code.visualstudio.com/) bzw. [VSCodium](https://vscodium.com/)
- Diverse kommerzielle IDEs (IntelliJ, PhpStorm, WebStorm) aus dem Hause [JetBrains](https://www.jetbrains.com/)
- Kommerzieller Editor [Sublime Text](https://www.sublimetext.com/)
- [Eclipse IDE](https://www.eclipse.org/eclipseide/)

---

# Setup: Visual Studio Code

Schon nach der Installation bietet Microsofts Visual Studio Code die notwendige Unterstützung zum Erstellen von Angular Anwendungen.

Folgende zusätzliche Plugins unterstützen die Developer Experience:
- [Angular Language Service](https://marketplace.visualstudio.com/items?itemName=Angular.ng-template)
- [EditorConfig](https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig)
- [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
- [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)

---

# Setup: Git

Homepage: https://git-scm.com/

Git als verteiltes Code-Versionsverwaltungssystem hat sich zum de-facto Standard entwickelt.

Es ist natürlich weder für die Schulung noch für die Entwicklung von eigenen Angular-Applikationen zwingend notwendig.

Allerdings erwartet die Angular CLI ein installiertes Git. Die Git-Initialisierung des Projektes lässt sich aber über eine Kommandozeilen-Option abschalten.

Außerdem sind meine Schulungsbeispiele allesamt Git-Repositories und profitieren von der Versionsverwaltung.

---

# Setup: Terminal

Bei der typischen Entwicklung von Angular Anwendungen werden immer wieder Kommandos auf einer Konsole/Shell ausgeführt.

Zwar bieten Editoren über Plugins bzw. IDEs die Möglichkeiten fast gänzlich ohne die Kommandozeilen-Befehle auszukommen. Dennoch empfehle ich für die Schulung die Verwendung eines geeigneten Terminals.

Alternativen:
- Windows Commandline (cmd)
- Powershell
- Git Bash (kommt mit der Git-Installation)
- WSL-Bash (Windows Subsystem für Linux)

Zum bequemeren Umgang mit den diversen Konsolen und Shells empfiehlt sich der neue [Windows Terminal](https://www.microsoft.com/de-de/p/windows-terminal/9n0dx20hk701).

---

# Setup: Powershell

Beim Einsatz der Powershell ist zu beachten, dass die Ausführungsrechte für Scripte konfiguriert sind:

```bash
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

---

# Setup: Proxy

Falls sich der Entwicklungsrechner hinter einem Firmen-Proxy befindet, müssen u.U. Konfigurationen der verwendeten Tools angepasst werden:

- npm:

  ```bash
  npm config set proxy http://username:password@host:port 
  npm config set https-proxy http://username:password@host:port
  ````

- git:

   ```bash
   git config --global http.proxy http://username:password@host:port 
   ```

Natürlich muss der Proxy im System selbst eingetragen sein. Diese Einstellungen werden zum Beispiel von Visual Studio Code übernommen.

---

# Hello Angular

- Erzeugen eines ersten Projektes
- Top-Level Projekt Struktur
- Source-Ordner Struktur
- Anwendungs-Struktur
- Building Blocks: Module und Komponenten

---

# Hello Angular: Projekt erzeugen I

Folgendes Kommando bitte in einem Terminal eingeben. Bei den folgenden Fragen zur Projekt-Konfiguration bitte einfach die Default-Werte mit `Enter` übernehmen.

```bash
ng new sample-schulung
```

Obiges Kommando funktioniert natürlich nur mit einer global installierten Angular CLI. Das Projekt wird dann genau gemäß der CLI-Version installiert.

Etwas flexibler ist man bei der Installation ohne globale CLI:

```bash
npx -p @angular/cli@latest ng new sample-schulung
```

Den Ausdruck `latest` kann man durch eine gewünschte Versionsnummer ersetzen (z.B. 10) oder einfach weglassen.

---

# Hello Angular: Projekt erzeugen II

Das `ng new sample-schulung` Kommando
- erzeugt ein neues Verzeichnis `sample-schulung`
- legt ein Anwendungsgerüst gemäß der gewünschten Angular-Version und den per Schalter angegebenen Optionen an
- installiert die Angular-Pakete und deren Abhängigkeiten
- initialisiert die Unit-Test Umgebung

Das ganze dauert je nach Rechner und Netztwerkgeschwindigkeit einige Sekunden ...

---

# Hello Angular:  Top-Level Struktur

```
├── package.json
├── tsconfig*.json
├── angular.json
├── karma.conf.js
├── node_modules/
├── src/
```

- `package.json`: Projekt Metadaten (NPM Module, Script-Kommandos, Autor, Lizenz, ...)
- `tsconfig*.json`: TypeScript Konfiguration
- `angular.json`: Angular CLI und Build Konfiguration
- `karma.conf.js`: Karma (Test Runner) Konfiguration
- `node_modules`: Verzeichnis mit den NPM Modulen (zur Zeit >400 MB groß)
- `src`: Verzeichnis mit dem Anwendungs-Sourcecode.

<style> pre { margin: 1rem 0;  } </style>

---

# Hello Angular:  Source-Ordner Struktur

```
├── src
│ ├── index.html
│ ├── main.ts
│ ├── polyfills.ts
│ ├── test.ts
│ ├── styles.css
│ ├── app/
│ ├── environments/
│ ├── assets/
```

- `index.html`: HTML-Startseite der Anwendung
- `main.ts`: Bootstrap-/Start-Script der Anwendung
- `polyfills.ts`: Browser-Polyfills (*Moltofill* für ältere Browser)
- `test.ts`: Start-Script der Unit-Tests
- `styles.css`: Globale Styles
- `app`: *Unser* Quellcode-Ordner
- `environments`: Die CLI unterstützt Umgebungen (**production**, **development**, **staging**, ...)
- `assets`: Statische Assets (Bilder, Fonts, ...)

<style> pre { margin: 1rem 0 ; } </style>

---

# Hello Angular: App-Ordner Struktur

```
├── src
│   ├── app
│   │   ├── app.component.css
│   │   ├── app.component.html
│   │   ├── app.component.spec.ts
│   │   ├── app.component.ts
│   │   ├── app.module.ts
```

- `app.module.ts`: Hauptmodul der Anwendung, Laden der notwendigen weiteren Module sowie Steuerung des Anwendungsstarts
- `app.component.ts`: Bootstrap-/Haupt-Komponente der Anwendung
- `app.component.html`: HTML-View/Ansicht der Haupt-Komponente
- `app.component.css`: Styles (lokal, gescoped) der Haupt-Komponente
- `app.component.spec.ts`: Test Spec der Haupt-Komponente

<style> pre { margin: 1rem 0 ; } </style>

---

# Hello Angular: Hauptmodul I

```ts {all|16}
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';

import { AppComponent } from './app.component';

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

<v-after>

Ein Modul wird wie jedes weitere Angular-Artefakt (Component, Directive, Pipe, Service) in einer TypeScript-Datei als Klasse deklariert und exportiert.

</v-after>

---

# Hello Angular: Hauptmodul II

```ts {1-4}
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';

import { AppComponent } from './app.component';

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

TypeScript Imports

---

# Hello Angular: Hauptmodul III

```ts {6-15}
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';

import { AppComponent } from './app.component';

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

<div class="my-2 text-sm">
TypeScript Decorator - Metadaten für Angular
</div>

<div class="text-sm">

<v-clicks>

- Welche Komponenten deklariert dieses Modul zur Verwendung?
- Welche weiteren Module werden importiert?
- Welche Komponente wird beim Anwendungsstart benötigt?

</v-clicks>

</div>

---
clicks: 5
---

# Hello Angular:  Komponenten I

```ts {1-10|3-7|4|5,6|8-10|9}
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'sample-schulung';
}
```

Aufbau einer Komponente

<ul>
  <li v-click="1">Component-Decorator</li>
  <li v-click="2" class="!ml-8">Selektor bestimmt, wo die Komponente eingesetzt wird.</li>
  <li v-click="3" class="!ml-8">Verweis auf externes Template und Stylesheets</li>
  <li v-click="4">Component-Class</li>
  <li v-click="5" class="!ml-8">Instanz-Daten (Property)</li>
</ul>

---

# Hello Angular: Komponenten II

```ts {all|5|6}
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  template: '<h1>{{title}}</h1>',          // inline HTML
  styles: ['h1 { font-weight: normal; }']  // inline styles
})
export class AppComponent {
  title = 'Hello Angular';
}
```

Template und Styles können auch inline definiert werden.

---
clicks: 1
---

# Hello Angular: Template Syntax I

```html {all|13}
<style>
  :host {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
      Helvetica, Arial, sans-serif,
       "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol";
  }
  h1, h2 {
    font-weight: 500;
  }
</style>

<h1>Angular Schulung</h1>
<h2>Projekt: {{ title }}</h2>
```

<div v-click="1" class="mt-2">

- `<h2>Projekt: {{title}}</h2>` ist eine *Interpolation*
- Der Ausdruck in `{{...}}` wird ausgewertet und das Ergebnis eingesetzt als Zeichenkette
- Symbole wie hier `title` werden in einem Kontext ausgewertet
- Der Kontext ist in diesem Fall die Componenten-Instanz
- Mehr zur Template-Syntax später ...

</div>

---

# Hello Angular: Template Syntax II

```html {1-10}
<style>
  :host {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
      Helvetica, Arial, sans-serif,
       "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol";
  }
  h1, h2 {
    font-weight: 500;
  }
</style>

<h1>Angular Schulung</h1>
<h2>Projekt: {{ title }}</h2>
```

Lokale Styles können auch inline im Template definiert werden.

Der Pseudo-Selektor `:host` bezieht sich dabei auf den äußeren Tag,
der die Komponente einsetzt und instanziiert.

---

# Hello Angular: Zusammenfassung

Komponenten sind die Hauptbausteine einer Angular-Anwendung

<v-clicks>

- Sie kapseln Datendarstellung und (zum Teil) Anwendungslogik
- Komponenenten werden in Modulen organisiert
- Jede Angular Anwendung hat ein Hauptmodul `AppModule` und eine Hauptkomponente, die im Hauptmodul deklariert wird und zum *Bootstrap* markiert wird.
- Eingesetzt wird diese im globalen `index.html`

</v-clicks>

---

# Hello Angular: Starten der Anwendung

- Start auf der Konsole über `npm start` oder `ng serve`
- Automatisierte Unit-Tests werden ausgeführt mit `npm test` oder `ng test`
- Production-Build erzeugen mit `npm run build` oder `ng build`

---

# Component Instance: Daten und Aktionen I

Wir füllen unsere Komponenten-Instanz mit etwas mehr Code.

```ts
export class AppComponent {
  // Properties
  title = 'Angular Grundkurs';
  learners: {firstname: string, lastname: string }[] = [];
  waitingList = [
    { firstname: 'George', lastname: 'Kalpakas' },
    { firstname: 'Pete', lastname: 'Darwin' },
    { firstname: 'Igor', lastname: 'Minar' },
    { firstname: 'Victor', lastname: 'Savkin' },
  ];
  // Methods
  summary(): string { 
    return `${this.learners.length} Teilnehmer, ${this.waitingList.length} in der Warteliste`;
  };
  addFromWaitingList(): void {
    this.learners = [ ...this.learners, ...this.waitingList.splice(0,1) ];
  }
}
```

---

# Component Instance: Daten und Aktionen II

- Daten die dargestellt werden können: Properties sowie Methoden und ihr Return-Wert[^1]
- Aktionen, die die Daten verändern: Schreibender Zugriff auf Properties sowie Methoden ohne Rückgabe

[^1]: Berechnende Methoden sind normalerweise keine gute Praxis. Wie wir noch sehen werden, wird die Methode unter Umständen sehr oft aufgerufen. Und zwar insbesondere wenn keine weiteren Vorkehrungen getroffen werden.

---

# Component Templates: Display Data I

Es gibt verschiedende Techniken, Daten darzustellen. Erste Variante ist die Interpolation von HTML-Textinhalt.

Syntax: `{{ expression }}`

```html
<h1>{{ title }}</h2>
<p>Zusammenfassung: {{ summary() }}</p>
```

---

# Component Templates: Display Data II

Um Listen bzw. aufzählbare Daten darzustellen kann eine sogenannte Direktive benutzt werden. Generell unterscheidet Angular zwischen Attribut-Direktiven und strukturellen Direktiven. Im Modul `@angular/common` stellt Angular einige Standard-Direktiven bereit - unter anderem die strukturelle Direktive `ngForOf`.[^1]

```html
<ul>
  <li *ngFor="let person of waitingList">{{  person.firstname }} {{ person.lastname }}</li>  
</ul>
```

Die Direktive erzeugt übrigens einen neuen Template-Kontext und in diesem in jedem Schleifendurchlauf eine neue Variable. In diesem Fall `person`

[^1]: Weitere Direktiven sowie eine nähere Bertrachtung der Syntax sowie der Unterschiede zwischen Attribut- und Strukturdirektiven werden im Beispielprojekt [Template-Syntax](https://github.com/lean-ng/edu-template-syntax) beleuchtet.

---

# Component Templates: Display Data III

Eine weitere strukturelle Direktive ist `*ngIf` zum bedingten Darstellen von Inhalten:

```html
<p *ngIf="learners.length === 0">Noch keine Teilnehmer.</p>
```

---

# Component Templates: Trigger Actions

Aktionen aus der Konponenten-Instanz (bzw. auf dem aktuellen Kontext) können u.a. über User-Events im Browser ausgelöst werden. Im Template wird über die Event-Binding Syntax das Event mit einem Template-Statement verknüpft.

Im Gegensatz zu Template-Expressions wird der Code erst mit dem Event evaluiert.

```html
<button (click)="addFromWaitingList()">Von Warteliste</button>
```

Nach der Ausführung des Statements überprüft Angular alle Bindungsausdrücke auf Veränderungen und rendert gegebenenfalls die Ausdrücke neu. 

Mehr zu Events sowie zu der sogenannten *Change-Detection*  später.

---

# Component Templates: Display Data IV

Daten können in unterschiedlichster Form verarbeitet werden (nicht nur interpoliert im Textinhalt). Eine weitere gängige Form der Bindungs-Techniken ist das **Property-Binding**.


```html
<button [disabled]="waitingList.length === 0" (click)="addFromWaitingList()">Von Warteliste</button>
```

Bei dieser Form werden Ausdrücke an DOM-Elementproperties gebunden. Ein gewisses Verständnis des HTML-DOM ist also recht hilfreich in der Angular-Programmierung <twemoji-winking-face />

---

# Component Templates: Zusammenfassung

Liste der Techniken:

- Interpolation
- Property Binding
- Attribute, Class and Style Bindings
- Event Binding
- Two-Way Binding
- Directives
- Template Reference Variables
- Template Expression Operators

---

# Component Templates: Links

- Einführendes Kapitel in der Dokumentation: [Templates Introduction](https://angular.io/guide/template-syntax)
- Referenz-Kapitel: [Binding Syntax](https://angular.io/guide/binding-syntax)
- Beispiel-Projekt: [Lean-NG/Template-Syntax](https://github.com/lean-ng/edu-template-syntax)
