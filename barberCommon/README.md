# BarberCommon — פרסומות משותפות למשחקי אבי וקוקו

מודול JavaScript ללא תלות בצד שרת, המשרת את המשחקים באתרי GitHub Pages.

## חיבור למשחק חדש

```html
<script src="https://shalevg12.github.io/barber-battle/barberCommon/ads.js?v=1"></script>
<script>
const ads = window.BarberCommonAds?.create({
  gameId: 'your-game-id',
  deathsPerAd: 2,
  durationSeconds: 15,
  skipAfterSeconds: 5,
  playerId: () => 'guest'
});
function onGameOver() { ads?.recordGameOver(); }
function onRemoveAdsClick() { ads?.removeAds(); }
</script>
```

- המודעה היא קומיקס מונפש מקורי של אבי וקוקו, עם שעון דילוג לאחר חמש שניות.
- מופיעה לאחר כל שתי פסילות **לכל משחק**. אין מודעה בכניסה או באמצע סיבוב.
- הסרת הפרסומות בחינם נשמרת במפתח `barberCommon:ads:v1` ב־localStorage, ומשותפת לכל משחקי GitHub Pages באותו דומיין, לאותו `playerId`.
- ללא התחברות, `guest` מזהה רק את הדפדפן המקומי. פטור ממודעות **לא מסתנכרן בין מכשירים**, ולא מהווה חשבון פרימיום מאומת. בעתיד ניתן להעביר את אחסון ההרשאות לשרת.
- בקוד משחק עתידי שמעביר `playerId`, העבירו מזהה קבוע רק אחרי זיהוי המשתמש.
- הסרטון המקורי הוא GIF של 9 תמונות, כ־14.4 שניות. הוא ארוז כ־WebP מונפש בתוך `ads.js`, ללא תלות חיצונית או תשלום.
- כרגע המודול מאוחסן תחת `barber-battle/barberCommon/` כדי לתת כתובת יציבה. לאחר שייווצר רפו נפרד `barberCommon`, אפשר להעביר אליו את אותו הקוד ולשנות כתובת סקריפט בלבד.