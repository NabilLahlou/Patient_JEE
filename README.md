# Patient_JEE
Application de gestion de patients réaliser en Java (Framework Spring)

- L'application de gestion des Patients a été réalisé avec le langage Java avec le Framework 'Spring',elle est composé des 4 dossiers (Entités,Repositories,Sécurité et Web) et d'une autre partie concernant les templates utilisés pour notre site web.

![image](https://user-images.githubusercontent.com/102859151/167722979-dc07c1ac-2ac1-4947-8be2-0ec5762ff611.png)
![image](https://user-images.githubusercontent.com/102859151/167723072-1404f10a-a72e-42e6-afa7-5874632fe387.png)

- Pour la partie entité, elle contient la classe Patient : Un patient est définie par son id,son nom,sa date de naissance,une option booléenne pour savoir si il est malade ou non ainsi que de son score.

![image](https://user-images.githubusercontent.com/102859151/167724111-a9f3c615-52db-40f7-8e4e-8daeb40d46c6.png)

- Annotations utilisées et explications :
- 1) @Entity             : Entity est une classe représentative (correspondant à) une table d'une base de données.
- 2) @Data               : Générer des méthodes pour les différents champs de la classe notamment les getters.
- 3) @AllArgsConstructor : L'annotation AllArgsConstructor permet de générer un constructeur avec toutes les variables de la classe.
- 4) @NoArgsConstructor  : NoArgsConstructor est utilisé pour générer des constructeurs sans paramètre.
- 5) @id                 : Afin que JPA le reconnaisse comme identifiant de l'objet. 
- 6) @GeneratedValue     : Pour indiquer que l'ID doit être généré automatiquement et de facon unique (Identity).
- 7) @NotEmpty           : Le champ ne doit pas etre vide.
- 8) @Size               : La taille du champ doit varié entre 4 et 40 caractères.
- 9) @Temporal           : Enregistre les dates en temps que jour / mois / année.
- 10)@DateTimeFormat     : Change le format de la date d'entrée en ("yyyy-MM-dd").
- 11)@DecimalMin         : Le score doit etre minimum de 100.

![image](https://user-images.githubusercontent.com/102859151/167727734-48413469-5977-4ff4-9b0f-569ae7b733b8.png)
 
 - La partie Repository :
 - Spring Data s’organise autour de la notion de repository. Il fournit une interface marqueur générique Repository<T, ID>. Le type T correspond au type de l’objet géré par le repository. Le type ID correspond au type de la clé d’un objet.
 
 ![image](https://user-images.githubusercontent.com/102859151/167728387-86a89b8e-288a-4f90-9d62-4b0683ea3902.png)

- La partie sécurité :
- La partie sécurité est divisée en trois parties :
  -Une partie entité qui contiendra les classes contenant les utilisateurs ainsi que le role de chaque utilisateurs (Deux classes dinstinctes (Roles et User)).
  -Une partie Repository pour implémenter les deux classes.
  -Une partie service qui exécutera des méthodes pour Ajouter/Supprimer des roles à un utilisateur.
  
  - Classe role : Un role est définit par son id,le nom du role et une description du role :
  
  ![image](https://user-images.githubusercontent.com/102859151/167730528-f77c321a-e4e7-4d50-9ebd-c262efd415f4.png)
  
  - Classe user : Un utilisateur est définit par son id,son nom d'utilisateur,son mot de passe,une option booléene pour savoir si le compte est actif ou non,et une liste des roles disponibles
  
  ![image](https://user-images.githubusercontent.com/102859151/167730847-f6db06f4-89d2-4397-a126-788bdee5d515.png)
  
  -Role repository : 
  
  ![image](https://user-images.githubusercontent.com/102859151/167731057-d05d508a-bba8-411d-b865-ac6432c4af31.png)
  
  -User repository :
  
  ![image](https://user-images.githubusercontent.com/102859151/167731101-daef3013-daf9-4c21-af08-506fac47bd41.png)
  
  -La partie Service :
   -Cette partie est composée d'une interface et de deux classes :
   -L'interface "SecurityService" permet de sauvegarder un nouvel utilisateur,un nouveau role.Ajouter un role à un utilisateur existant,supprimer un role à un utilisateur existant.
   
   ![image](https://user-images.githubusercontent.com/102859151/167731818-786cff6a-9373-4317-a3c6-cb3c276f8758.png)
   
   -La classe SecurityServiceImpl contiendra les méthodes cités précédemment:
    -Méthode saveNewUser :
    ![image](https://user-images.githubusercontent.com/102859151/167732001-b380513b-e522-4344-9b77-c002ea516ed9.png)
    
    -Méthode saveNewRole :
    ![image](https://user-images.githubusercontent.com/102859151/167732062-89cc0c9a-799e-47d6-9af7-10b6baff32a3.png)
    
    -Méthode addRoleToUser :
    ![image](https://user-images.githubusercontent.com/102859151/167732106-6a2028a2-0449-4d62-af9c-8205d9b84afa.png)
    
    -Méthode removeRoleFromUser: 
    ![image](https://user-images.githubusercontent.com/102859151/167732166-346cd248-b68d-409f-8f18-6b0ac2793f58.png)
    
    - Un fichier SecurityConfig pour gérer l'accès aux ressources :
    
    ![image](https://user-images.githubusercontent.com/102859151/167732426-2fc2a65e-8ee3-495f-91f7-c269c84d34c7.png)
    
    -Par exemple pour une url se terminant par "/",tout les utilsateurs (Normaux et Admins) y auront accès,pour une url "/admin/** " seul les administrateurs peuvent y avoir accès,une url "/user/** " seul les utilisateurs normaux etc...
    
    ![image](https://user-images.githubusercontent.com/102859151/167732631-c4984164-f2f6-49df-9f2e-99d408d8c1c3.png)
    
    -La partie web est composé de deux controllers,un concernant les patients et un autre concernant la sécurité 
     -PatientController : C'est là ou nous ferons le mapping des différentes pages HTML : Ajouter un patient via un formulaire,la page principale,modifier un patient,l'index....
      -index:      
      ![image](https://user-images.githubusercontent.com/102859151/167737741-f83c50c1-1d48-4cb7-a79e-93f64af6dec1.png)
      
      -delete: 
      <img width="397" alt="delete" src="https://user-images.githubusercontent.com/102859151/167738198-8acaf6e1-db86-4439-80db-135ed49d3950.PNG">
      
      -/:
      ![image](https://user-images.githubusercontent.com/102859151/167737820-e9301d16-8718-43fd-9128-8abc2f2db06a.png)
      
      -patients:
      ![image](https://user-images.githubusercontent.com/102859151/167737854-c07b1b0c-0338-424a-af0b-f35e1576e345.png)
      
      -formPatients:
      ![image](https://user-images.githubusercontent.com/102859151/167737878-67ee5337-c806-42aa-9bbb-eff088046218.png)
      
      -save:
      ![image](https://user-images.githubusercontent.com/102859151/167737960-65a68eb9-d4a4-4e0a-b9bb-e464c3ee1604.png)
      
      -editPatient:
      ![image](https://user-images.githubusercontent.com/102859151/167737999-5f8432e2-e921-4c1c-84a6-69b42051f115.png)

     -SecurityController: C'est là ou nous ferons le mapping de la page de sécurité :
     ![image](https://user-images.githubusercontent.com/102859151/167734741-a9107449-a17a-45a0-91b5-7a9ff9bc2fbf.png)
     
     - Dans le fichier PatientMvcApplication,on va manuellement ajouter plusieurs patients au niveau de la base de données ainsi que plusieurs utilisateurs afin de tester si l'application marche ou non.L'annotation @Bean permet d'executer des commandes à chaque lancement de l'application 
     
     - Ajout de patients:
     ![image](https://user-images.githubusercontent.com/102859151/167736089-9b54c973-ca96-4273-a32a-dae6c90acfeb.png)
     
     -Ajout des users et role:
     ![image](https://user-images.githubusercontent.com/102859151/167736352-9edee195-21b7-456b-859b-0e77d04c6605.png)
     
     -Pour ce qui est des pages HTML,elles sont présentes dans le dossier template qui contient la page d'accueil,le formulaire des patients,la page de modifications...
     
     ![image](https://user-images.githubusercontent.com/102859151/167737097-8fcd2a8f-b1b7-4f34-a933-84dd44b134d0.png)
     
     -Ces pages HTML sont intégrés au niveau du repository GitHub 





   

  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
