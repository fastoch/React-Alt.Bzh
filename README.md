# Intro 

prof = Nicolas Acard 
premier jour = 18 août 2025   
durée = 2 semaines  

Autrefois, le contenu frontend était généré dynamiquement par le backend, sous forme de code HTML + CSS + JS.  
Mais une application mobile ou desktop ne reconnaît pas ce type de code...  

De nos jours, on développe des **SPAs** (single page applications) avec des frameworks comme React.  
Et le backend renvoie du **JSON** au lieu de générer et de renvoyer lui-même du HTML+CSS+JS.  

# Project Setup (Vite + React + TS)

- installer **Node.js** pour pouvoir exécuter du JS localement
  - l'install de Node s'accompagne souvent de l'install de **npm** (Node Package Manager)
- on va aussi utiliser **Vite** pour initialiser et développer notre projet React 
  - `npm create vite@latest` --> React + **TypeScript**
  - project name = 'react-allocine'
- `cd react-allocine`
- `npm i` pour installer les dependencies (listées dans notre package.json)
  - ça crée un gros dossier nommé 'node_modules' dans lequel sont installés les dependencies
- Lancer l'application en mode dev via `npm run dev` --> http://localhost:5173
- on va aussi utiliser **TailwindCSS**
  - installer Tailwind via un terminal: `npm i tailwindcss @tailwindcss/vite`
  - configurer le fichier vite.config.ts en ajoutant tailwindcss aux imports et à la liste des plugins:
    ```ts
    import { defineConfig } from 'vite'
    import react from '@vitejs/plugin-react'
    import tailwindcss from '@tailwindcss/vite'
    
    // https://vite.dev/config/
    export default defineConfig({
      plugins: [
        tailwindcss(),
        react()
      ]
    })
    ```
  - enfin, importer tailwindcss au début de notre fichier /src/index.css: `@import "tailwindcss";`
  - on peut effacer le CSS déjà présent par défaut dans index.css 

# Correction Exercice du mardi 19 août

https://git.alt-tools.tech/bettercallsoul-bytemerenf/allocine/-/tree/session2?ref_type=heads 

# React router

Section à compléter...

# React-hook-form (25 août)

- install the library: `npm install react-hook-form`
- 

# Cycle de vie d'un composant

- Initialisation (le composant est "monté")
- Update (re-render)
- "Destruction" (n'est plus affiché)

# Fonctionnement de `useEffect(() => {}, [])`

# Envoyer des requêtes HTTP

# Axios

- exécuter `npm i axios` pour l'installer
- ajouter `import axios from 'axios';` dans le fichier .tsx concerné 

Exemple:  
<img width="714" height="437" alt="Axios_exemple" src="https://github.com/user-attachments/assets/a58d3cb8-be91-452f-bdcb-049ec3b3730c" />

En pratique, les fonctions comme `getMovies` sont placées dans un dossier `/src/services`, dans un fichier `api.ts`.  
NE PAS OUBLIER d'exporter ces fonctions afin de pouvoir les importer ensuite dans les différents composants.  

Exemple 2:  
<img width="904" height="457" alt="Axios_exemple2" src="https://github.com/user-attachments/assets/789aad4e-0deb-4bf3-a02f-0e7e0c70edba" />

# Travail pour appliquer le cours du 26 août

Sur le projet suivant: https://git.alt-tools.tech/gp-better-code-soul/React_movie_app  

- fetch popular movies + movieDetails from TMDB's API
- use axios and `useEffect(() => {}, [])`

# 27 août - Retirer la logique de App.tsx 

L'objectif est de n'avoir dans le composant `App` rien d'autre que les routes... et les contextes (qu'on va voir aujourd'hui).    

Lien utile: https://deku.posstree.com/en/react/context-api/  
"Let's see how to use Context API to manage the global data in React."  

Un contexte peut être vu comme un "utérus" et le `useContext()` est le cordon ombilical qui relie un contexte à un composant.  
Le contexte est implémenté dans un fichier dédié (comme `CounterProvider`) au sein d'un dossier `Contexts`.  
Et le branchement avec `useContext()` se fait au niveau du composant qu'on veut "brancher".  

Exemple de contexte avec un fichier `WishlistProvider.tsx`:
```tsx
import { createContext } from "react";

export const WishlistContext = createContext();

const WishlistProvider = ({children}) => {
  const [wishlist, setWishlist] = useState<MovieInterface[]>([])
  const updateWishlist = () => {

  }

  return (
    <WishlistContext value={{wishlist, updateWishlist}}>

    </WishlistContext>
  )
}
```

Ensuite, on branche ce contexte au composant `NavBar.tsx`:
```tsx
const NavBar = () => {
  const {wishlist, updateWishlist} = useContext(WishlistContext)
}
```

Enfin, on ajoute le nouveau contexte dans `App.tsx`:
```tsx

```

Le code du prof est consultable ici:  
https://git.alt-tools.tech/bettercallsoul-bytemerenf/allocine/-/tree/session7?ref_type=heads    

Pour cet après-midi (27 août), je peux clone le repo "session6" du prof et regarder ce qu'il a fait sur la branche "session7".  

Consignes:
- incrémenter le compteur de Likes sur tous les films à la fois quand on like n'importe quel film
- implémeter les contextes WishListProvider et LikeCounterProvider
- faire en sorte qu'on ne puisse pas ajouter des films déjà présents dans la wishlist

---
EOF
