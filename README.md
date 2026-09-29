hi

## Vidéos pilotées par le défilement (page d'accueil)

Le site s'ouvre sur deux vidéos que la molette (ou le doigt sur téléphone) fait avancer et reculer :

1. **L'enveloppe** : une enveloppe ivoire au rabat de dentelle, scellée du cachet nacré I&A, s'ouvre ;
   le carton « Nous nous marions · Ines & Alan · 11 · 09 · 2027 » en sort puis se lève face à l'écran.
   Le menu est masqué pendant l'ouverture ; le lien « Passer » mène directement aux alliances.
   Si `musiqueAuto: true`, la musique se lance quand le rabat s'ouvre.
2. **Les alliances** : deux alliances séparées se rejoignent.

Fichiers de l'enveloppe : `video/enveloppe-large.*`, `video/enveloppe-mobile.*` (même principe que ci-dessous).

- `video/alliances-large.mp4` / `.webm` : écrans larges (1920 × 1080)
- `video/alliances-mobile.mp4` / `.webm` : téléphones en portrait (1080 × 1920)
- `video/*-debut.jpg` et `*-fin.jpg` : première et dernière image (affiche, et image fixe si « réduire les animations » est activé)

Chaque image de la vidéo est une image clé : c'est ce qui rend le défilement fluide dans les deux sens.
Pour remplacer la vidéo par la vôtre, gardez les mêmes noms de fichiers et ré-encodez-la ainsi :

```
ffmpeg -i ma-video.mp4 -an -c:v libx264 -crf 24 -g 1 -bf 0 -pix_fmt yuv420p -movflags +faststart video/alliances-large.mp4
ffmpeg -i ma-video.mp4 -an -c:v libvpx-vp9 -b:v 0 -crf 32 -g 1 video/alliances-large.webm
```

La longueur du défilement se règle dans `index.html` : `.alliances{height:340vh}` (plus grand = plus lent).
