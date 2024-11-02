# Vue 3 + Vite + TailwindCss

Voici le lien sur Netlify de mon site web : Test-GCTech[https://test-gctech-manoa.netlify.app/].

## Les choix utilisés

- Affichage d'une card (Paris) avec les données dans un fichier .js (data/tourismInfos.js) permettant la réutilisation du composant TourismCard.vue avec de nouvelles données.

- Utilisation au maximum des styles Tailwind au lieu du style css classique via la balise "style" de Vue3.

- State gérer en locale avec Ref et utilisation des defineProps pour passer les éléments entre parents et enfants. Simplicité d'utilisation dans le contexte d'un petit site web avec une page.

- Accessibilité bonne avec le support du clavier dans la navigation.

## Les fonctionnalités ajoutés + bonus

- Ajout d'un carousel pour l'affichage de plusieurs images correspondant aux activités possible dans la ville.

- Ajout d'un affichage de notation pour une future intégration d'un formulaire de notation possible.

- Ajout d'un 'Header' et 'Footer' pour une uniformité visuelle de la page et attirer de l'audience avec des couleurs peu aggressive et cohérente avec un site de voyage.

- Ajout d'une animation sur le 'toggle' bouton + du hover sur les liens cliquables

- Ajout d'une transition fluide sur l'ouverture / fermeture du 'toggle' bouton.

## Explications des choix

J'ai choisis l'ajout de certaines features dans la création de la page web pour avoir une navigation fluide et cohérente avec les sites de voyage.

De plus, j'ai choisis d'utilisé Vite avec VueJS pour simplifier le build d'une petite application.
