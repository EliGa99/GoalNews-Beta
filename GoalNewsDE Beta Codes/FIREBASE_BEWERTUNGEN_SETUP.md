# GoalNews-Bewertungen: Firebase-Regeln

Die vollständigen, zusammenhängenden Firestore-Regeln stehen in `firestore.rules`. Bewertungen sind öffentlich lesbar; angemeldete Nutzer können nur ihre eigene Bewertung erstellen oder aktualisieren.

Veröffentliche in Firebase Console → **Firestore Database** → **Rules** immer die ganze Datei `firestore.rules`. Lass die frühere globale Wildcard-Regel nicht zusätzlich bestehen, da sie die eingeschränkten Regeln aushebeln würde.
