In Angular kann man verschiedene Konfigurationen für sein Projekt definieren. Zum Beispiel will man verschiedene API-Keys und verschiedene URLs verwenden. 
Die meisten Anwendungen unterscheiden zwischen einer Umgebung für Development, einer Umgebung für Staging und einer Umgebung für produktiven Code.

Die [[Angular-CLI]] kann Dateien je nach Umgebung austauschen. So werden immer die richtigen Werte verwendet.
# Angular CLI Konfiguration
Die [[Angular-CLI]] unterstützt ein Konfigurationsobjekt, mit dem man bestimmte Optionen setzen kann, die auf der Konfiguration (Test/Staging/Prod) basieren, die in der Command-Line angegeben werden.
```TypeScript
{
  "projects": {
    "my-app": {
      "architect": {
        "build": {
          "builder": "@angular-devkit/build-angular:browser",
          "options": {
            // By default, disable source map generation.
            "sourceMap": false
          },
          "configurations": {
            // For the `debug` configuration, enable source maps.
            "debug": {
              "sourceMap": true
            }
          }
        },
        ...
      }
    }
  }
}
```

Mit dem folgenden Befehl kann man bestimmen, welche Konfiguration die [[Angular-CLI]] verwenden soll: 
```Bash
ng build --configuration debug
```
# Konfigurationsdateien erstellen
Angular unterstützt den Austausch von Dateien anhand der definierten Konfiguration.

Zunächst muss man den ```src/environments/```-Ordner erstellen. Der folgende Befehl generiert den Ordner, in dem die Environments definiert und konfiguriert werden können.
```Bash
ng generate environments
```
 Jede Umgebung hat ihre eigenes Konfigurationsobjekt in einer eigenen Datei. Dafür muss man den Namen der Umgebung auf folgende Weise in den Dateinamen integrieren:
```
my-app/src/environments
├── environment.development.ts
├── environment.staging.ts
└── environment.ts
```
# Environment-spezifische Werte definieren
Die grundlegende Datei des 'environments'-Ordner ist 'environment.ts' und enthält die standart-Umgebungseinstellungen, zum Beispiel:
```TypeScript
export const environment = {
	production: true,
	apiUrl: 'http://my-prod-url'
};
```
Man kann Werte überschreiben, sodass sie in anderen Umgebungen anders sind.
Beispielsweise könnte man in ```environments.development.ts``` eine andere Url für die API definieren:
```TypeScript
export const environment = {
  production: false,
  apiUrl: 'http://my-dev-url'
};
```
> [!NOTE] Ist keine bestimmte Umgebung definiert, nutzt die [[Angular-CLI]] die Datei 'environment.ts' als ihr build target. 
# Environment-spezifische Werte nutzen
Um Werte aus den Konfigurationsdateien zu nutzen, muss man im Component die originale Environment-Datei importieren:
```TypeScript
import { environment } from './environments/environment';
```
Nun kann man die im Konfigurationsobjekt definierten Werte nutzen:
```TypeScript
import { environment } from './../environments/environment';

// Fetches from `http://my-prod-url` in production, `http://my-dev-url` in development.
fetch(environment.apiUrl);
```
# Wie der Austausch im Hintergrund funktioniert
In den vorherigen Abschnitten wurde erklärt, dass Angular die Konfigurationsobjekte automatisch austauscht. Je nach Environment wird ein ein anderes Objekt bzw. eine andere Datei verwendet. 

Dieser Austausch kann auch konfiguriert werden. In der Datei 'angular.json' befindet sich ein Abschnitt namens 'fileReplacements'. Dort kann man für jede Datei der Applikation eine Environment-Spezifische Version dieser Datei definieren. 

Wenn man die Konfiguration der Environments mit ```ng generate environments```erstellt, wird 'Angular.json' automatisch angepasst. Man kann diese verändern oder neue Ersatzdateien hinzufügen, indem man 'Angular.json' direkt verändert.
```JSON
"configurations": {
    "development": {
      "fileReplacements": [
          {
            "replace": "src/environments/environment.ts",
            "with": "src/environments/environment.development.ts"
          }
        ],
	    ...
```
Im oberen Beispiel wird 'environment.ts' mit 'environment.development.ts' ersetzt, wenn man die Applikation mit 'ng build --configuration development' verwendet.

Will man bei diesem Beispiel noch eine Konfiguration für 'staging' hinzufügen, muss man 'Angular.json' auf folgende Weise erweitern:
```JSON
"configurations": {
    "development": { … },
    "production": { … },
    "staging": {
      "fileReplacements": [
        {
          "replace": "src/environments/environment.ts",
          "with": "src/environments/environment.staging.ts"
        }
      ]
    }
  }
```
Nun kann man die Applikation mit 'ng build --configuration staging' starten. Es wird nun 'environment.staging.ts' verwendet.
# Environment mit 'ng  serve' wählen
Der Befehl 'ng serve' nutzt normalerweise den Development-Build des Projekts.
Will man das ändern, muss man die Option 'buildTarget' ändern:
```JSON
"serve": {
    "builder": "@angular-devkit/build-angular:dev-server",
    "options": { … },
    "configurations": {
      "development": {
        // Use the `development` configuration of the `build` target.
        "buildTarget": "my-app:build:development"
      },
      "production": {
        // Use the `production` configuration of the `build` target.
        "buildTarget": "my-app:build:production"
      }
    },
    "defaultConfiguration": "development"
  },
  ```
  



