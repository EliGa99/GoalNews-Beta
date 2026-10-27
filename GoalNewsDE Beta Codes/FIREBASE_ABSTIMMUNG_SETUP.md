# Spieltipps: Firebase-Regeln

Die vollständigen, zusammenhängenden Firestore-Regeln stehen in `firestore.rules`. Für die Spieltipps erlauben sie angemeldeten Konten eine eigene Stimme pro Spiel; nachträgliches Ändern oder Löschen wird abgelehnt.

Veröffentliche in Firebase Console → **Firestore Database** → **Rules** immer die ganze Datei `firestore.rules`. Die frühere globale Wildcard-Regel darf nicht zusätzlich bestehen bleiben: passende `allow`-Regeln werden mit ODER verknüpft und eine globale Freigabe würde engere Regeln umgehen.
