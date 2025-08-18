# Intro 

prof = Nicolas Acard (prof Nextech Avignon)  
premier jour = 18 août 2025   
durée = 2 semaines  

Autrefois, le contenu frontend était généré dynamiquement par le backend, sous forme de code HTML + CSS + JS.  
Mais une application mobile ou desktop ne reconnaît pas ce type de code...  

De nos jours, on développe des **SPAs** (single page applications) avec des frameworks comme React ou React Native (mobile).  
Et le backend renvoie du **JSON** au lieu de générer et de renvoyer lui-même du HTML+CSS+JS.  

# Setup (Vite + React + TS)

- installer **Node.js** pour pouvoir exécuter du JS localement
  - l'install de Node s'accompagne souvent de l'install de **npm** (Node Package Manager)
- on va aussi utiliser **Vite** pour initialiser et développer notre projet React 
- `npm create vite@latest` --> React + **TypeScript**
- `cd <project_folder>`
- `npm i` pour installer les dependencies (listées dans notre package.json)
- `npm run dev` --> http://localhost:5173
- on va aussi utiliser **TailwindCSS**
