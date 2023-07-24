
![logo_ironhack_blue 7](https://user-images.githubusercontent.com/23629340/40541063-a07a0a8a-601a-11e8-91b5-2f13e4e6b441.png)

# LAB | Vue.js Tweets (Composition API)

## Einführung

Das Durchreichen von Daten über _props_ ist ein wichtiges Vue.js-Konzept, das am besten durch praktische Übungen verstanden wird. Wir werden diese Übung nutzen, um dein Verständnis von Props zu festigen.

Wir werden ein vorhandenes Stück UI von einer beliebten App, Twitter, klonen. Los geht's!

<p align="center">    
 <img src="https://education-team-2020.s3.eu-west-1.amazonaws.com/web-frontend-vue/lab-vue-tweets-4.png" width="500"> </p>   

## Anforderungen

- Forke dieses Repo
- Klone dieses Repo
- Öffne das LAB und starte:

  ```bash
  $ cd lab-vue-c-tweets
  $ npm install
  $ npm run dev
  ```

## Abgabe

- Nach Fertigstellung führe folgende Befehle aus:

  ```bash
  git add .
  git commit -m "done"
  git push origin main
  ```

- Erstelle einen Pull Request, damit deine TAs deine Arbeit überprüfen können.

## Erste Schritte


1. Wir werden [Font Awesome](https://fontawesome.com/v5.15/icons?d=gallery&p=1) für die Icons in unserer App verwenden. Füge das folgende Stylesheet im `head` der `index.html` Seite hinzu:

   ```html
       <link
         rel="stylesheet"
         href="https://pro.fontawesome.com/releases/v5.10.0/css/all.css"
         integrity="sha384-AYmEC3Yw5cVb3ZcuHtOA93w35dYTsvhLPVnYs9eStHfGJvOvKxVfELGroGkvsg+p"
         crossorigin="anonymous"
       />
   ```

## Anweisungen

### Iteration 1 | Anfänglicher Inhalt

Damit du dich auf Vue.js konzentrieren kannst, ohne dir Gedanken über die Formatierung machen zu müssen, haben wir dir die CSS-Styles zur Verfügung gestellt. Alle CSS-Stile sind im Starter-Code in der `src/App.vue` Datei innerhalb des `<style>` Tags enthalten.

Wir haben dir auch den anfänglichen Inhalt der `App.vue` zur Verfügung gestellt und die HTML-Struktur für die  `Tweet.vue` Komponente eingefügt. Bevor du anfängst zu arbeiten, nimm dir einen Moment Zeit, um diese beiden Dateien durchzusehen.

Wenn du die App zunächst ausführst, solltest du Folgendes sehen:

![Tweet component after the initial setup](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-frontend-vue/lab-vue-tweets-1.png)


Die `Tweet` Komponente zeigt im Moment statischen Inhalt an. Wir werden dies in der nächsten Iteration ändern. Wir werden die `Tweet` Komponente aktualisieren, um den Inhalt anzuzeigen, der von den `props` kommt.

### Iteration 2 | Den Tweet als Prop übergeben

In `App.vue` haben wir ein Array namens `tweetsArray`, das Objekte repräsentiert, die Tweets darstellen. Wir werden die `Tweet` Komponente verwenden, um diese _tweet_ Objekte anzuzeigen. In der `Tweet` Komponente werden wir den `name` des Benutzers, das `image` des Benutzers, den `handle` des Benutzers, den `timestamp` des Tweets und die `message` anzeigen.

**Den Tweet als Prop übergeben**

Übergebe das erste Datenobjekt aus den `tweets` als Prop an die `Tweet` Komponente:

```vue
<!-- src/App.vue -->
<!-- ... -->

<Tweet :tweet="tweets[0]" />
```

**Den Tweet-Inhalt in der `Tweet` Komponente anzeigen**

Aktualisiere die `Tweet` Komponente, um die Werte aus der `tweet` Prop anzuzeigen. Denke daran, dass der übergebene Wert ein Objekt ist.

**Erwartetes Ergebnis**

Nachdem du fertig bist, sollte deine `Tweet` Komponente den folgenden Inhalt anzeigen:

![Tweet component after passing the "tweets" prop](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-frontend-vue/lab-vue-tweets-2.png)



### Iteration 3 | Erstellen der Komponenten

Wir werden nun neue Dateien für die Komponenten erstellen, die wir in den folgenden Iterationen erstellen werden. Erstelle innerhalb des Ordners `src/components/` die folgenden neuen Dateien:

- `src/components/ProfileImage.vue` ,
- `src/components/User.vue` ,
- `src/components/Timestamp.vue` ,
- `src/components/Message.vue` and
- `src/components/Actions.vue`.


In den folgenden Iterationen musst du die `Tweet` Komponente überarbeiten. Du wirst aufgefordert, Teile der vorhandenen HTML-Struktur in neue Komponenten zu extrahieren:

![Example - Refactoring the "Tweet" component](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-frontend-vue/lab-vue-tweets-3.png)    
<br>


**Wenn alle Iterationen abgeschlossen sind**, wird die endgültige Version deiner `Tweet` Komponente so aussehen:

<details> <summary>Klicke, um den Code zu sehen</summary>  

```vue
<!-- FINAL VERSION -->

<template>
  <div class="tweet">
    <ProfileImage image="user.image" />

    <div class="body">
      <div class="top">
        <User userData="user" />
        <Timestamp time="timestamp" />
      </div>

      <Message message="message" />
      <Actions />
    </div>

    <i class="fas fa-ellipsis-h"></i>
  </div>
</template>

<script>
  const props = defineProps({
    user: Object,
    timestamp: String,
    message: String
  });
</script>
```  

:heavy_exclamation_mark: Kopiere den obigen Code nicht direkt in die `Tweet` Komponente!

Du wirst es in den nächsten Iterationen Schritt für Schritt tun. Du wirst die Teile des HTML ersetzen, während du jede neue Komponente erstellst.

<hr>
<br> 
</details>   

### Iteration 4 | ProfileImage Komponente

**HTML extrahieren**

Extrahiere das vorhandene `img` Tag und rendere es durch die `ProfileImage` Komponente:

```jsx
<img src="IMAGE_URL" class="profile" alt="profile"/>
```  

**Komponente rendern**

Wenn du fertig bist, importiere die `ProfileImage` Komponente in `Tweet.js`. Nach dem Importieren rendere die Komponente innerhalb von `Tweet` auf folgende Weise:

```vue
<!-- ... -->
<template>
  <div class="tweet">
    <ProfileImage image="user.image" />
<!-- ... -->
```  

**Auf die Props zugreifen**

`ProfileImage` erhält eine Prop `image`. Setze diesen Wert als `src` des `<img />` Tags.

### Iteration 5 | User Component


**HTML extrahieren**

Extrahiere die vorhandenen `span` Tags, die die Benutzerinformationen anzeigen, und rendere sie durch die `User` Komponente:

```vue
<span class="user">
  <span class="name"> USER_NAME </span>
  <span class="handle">@ USER_HANDLE</span>
</span>
```   

**Komponente rendern**

Importiere die `User` Komponente in `Tweet.js`. Nach dem Importieren rendere die Komponente innerhalb von `Tweet` auf folgende Weise:

```vue
<!-- ... -->

<template>
  <div class="tweet">
    <ProfileImage image="user.image" />

    <div class="body">
      <div class="top">
        <User userData="user" />

<!-- ... -->
```

**Auf die Props zugreifen**

Wir haben das Objekt mit den Benutzerinformationen über die Prop `userData` übergeben. Greife auf den _name_ und den Twitter-_handle_ des Benutzers zu und zeige sie an.




### Iteration 6 | Timestamp Komponente

**HTML extrahieren**

Extrahiere das vorhandene `span` Tag, das die _timestamp_ Informationen anzeigt, und rendere es durch die `Timestamp` Komponente:

```jsx
<span class="timestamp"> TWEET_TIMESTAMP </span>
```  

**Komponente rendern**

Importiere die `Timestamp` Komponente in `Tweet.js`. Nach dem Importieren rendere die Komponente innerhalb von `Tweet` auf folgende Weise:

```vue
<!-- ... -->

<template>
  <div class="tweet">
    <ProfileImage image="user.image" />

    <div class="body">
      <div class="top">
        <User userData="user" />
        <Timestamp time="timestamp" />

<!-- ... -->
```  

**Auf die Props zugreifen**

`Timestamp` erhält eine Prop `time`. Zeige diesen Wert als Inhalt des `span` Tags an.


### Iteration 7 | Message Komponente

**HTML extrahieren**

Extrahiere das vorhandene `p` Tag und rendere es durch die `Message` Komponente:

```jsx
<p class="message"> TWEET_MESSAGE </p>
```  

**Komponente rendern**

Wenn du fertig bist, importiere die `Message` Komponente und rendere sie in `Tweet.js` auf folgende Weise:


```vue
<!-- ... -->

<template>
  <div class="tweet">
    <ProfileImage image="user.image" />

    <div class="body">
      <div class="top">
        <User userData="user" />
        <Timestamp time="timestamp" />
      </div>

      <Message message="message" />
<!-- ... -->
``` 

**Auf die Props zugreifen**

`Message` erhält eine Prop `message`. Zeige diesen Wert im `p` Tag an.



### Iteration 8 | Actions Komponente

**HTML extrahieren**

Extrahiere das vorhandene `div.actions` Tag der Nachricht und rendere es durch die `Actions` Komponente:

```jsx
    <div class="actions">
      <i class="far fa-comment"></i>
      <i class="fas fa-retweet"></i>
      <i class="far fa-heart"></i>
      <i class="fas fa-share"></i>
    </div>
```  

**Komponente rendern**

Wenn du fertig bist, importiere die `Actions` Komponente und rendere sie in `Tweet.js` wie folgt:

```vue
<!-- ... -->

<template>
  <div class="tweet">
    <ProfileImage image="user.image" />

    <div class="body">
      <div class="top">
        <User userData="user" />
        <Timestamp time="timestamp" />
      </div>

      <Message message="message" />
      <Actions />

<!-- ... -->
```  
Die `Actions` Komponente nimmt keine Props entgegen.

### Iteration 9 | Mehrere `Tweet`s rendern

Sobald du mit dem Refactoring der `Tweet` Komponente fertig bist, aktualisiere `App.vue`, um drei `<Tweet />` Komponenten anzuzeigen. Jede `<Tweet />` sollte ein separates _tweet Objekt_ aus dem `tweetsArray` erhalten.

Wenn du fertig bist, sollte deine App den folgenden Inhalt anzeigen:

<details>   
<summary>Klicke, um das Bild zu sehen</summary>   

![Example - Final Result](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-frontend-vue/lab-vue-tweets-4.png)


</details>   

<hr>   

**Viel Spaß beim Coden!** :heart: