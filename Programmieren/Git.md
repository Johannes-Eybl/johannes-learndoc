
IMMER *COMMIT → PULL → PUSH*

###### Bsp: Lars und Rolf arbeiten an einem Projekt. Rolf hat das Projekt erstellt.

- Rolf ändert etwas am Projekt und fügt das mit `git add` (Auswählen, was geändert wird) und `git commit`(Das ausgewählte commiten) zum gemeinsamen Projekt hinzu. (Git commit fügt die Neuerung nur zum *lokalen* hinzu)
- Dieser *commit* ist aber nur mit `git push` für alle verfügbar.
- Lars kann nun mit `git pull` diese Änderung auf den eigenen PC laden. Dieser Befel ist “Update Project” in IntelliJ.

**Wenn beide Seiten das gleiche verändern, ist kein Push möglich! Dann muss ein Merge gemacht werden!**

# Befehle

| Befehl                                                       | Beschreibung                                                                                                                                                                               |
| ------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `git config --global user.name "Nachname Vorname"`           | Name konfigurieren (einmal)                                                                                                                                                                |
| `git config --global user.email "vorname.nachname@email.ch"` | EMail konfigurieren (einmal)                                                                                                                                                               |
| `git clone url`                                              | Repository initial klonen                                                                                                                                                                  |
| `git status`                                                 | Was ist los?                                                                                                                                                                               |
| `git pull`                                                   | Server -> Lokal                                                                                                                                                                            |
| `git add path`                                               | Files zum Speichern auswählen.                                                                                                                                                             |
| `git commit`                                                 | Speicherpunkt erstellen                                                                                                                                                                    |
| `git commit --amend --no-edit`                               | Adds a change to the last commit. _WARNING_: Never use on pushed commits!                                                                                                                  |
| `git push`                                                   | Lokal -> Server                                                                                                                                                                            |
| `git branch`                                                 | Welche Branches gibt es?                                                                                                                                                                   |
| `git checkout branchName`                                    | Wechsle genutzten Branch zu brancName                                                                                                                                                      |
| `git checkout -b newBranchName`                              | Erstelle neuen Branch und wechsle direkt zu diesem                                                                                                                                         |
| `git revert commitId`                                        | Undoes the Commit with corresponding commit-id. Creates a new commit and cancels out the changes made in the target commit. Useful for undoing changes without altering the commit history |
| `git reset`                                                  | Rewinds the Project History to a particular point. Moves the HEAD and the branch pointer to a specific commit. Useful for unstaging changes while keeping them in the working dir!         |
| `git reset commitId`                                         | Unstages commit with corresponding id                                                                                                                                                      |
| `git reset --soft HEAD~1`                                    | Rewind to on before the current Version/Commit                                                                                                                                             |
# Rebase für Branches von Branches
Manchmal erstellt man Branches als Branches von anderen Branches.

Diese Branches enthalten die Commits der originalen Branches, was bei einem Merge problematisch sein kann - besonders, wenn der originale Branch bereits gemerged wurde. 

Der neuste Branch ist also "verschmutzt" mit den Commits, die bereits im "main" sind.

