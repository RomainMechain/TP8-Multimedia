# TP8-Multimedia 

## Maillage 

Pour afficher ce cube, il suffit de définir les coorddonées de toute les points de chaque face dans le verticesCarreDoublons : 

```cpp
std::vector<float> verticesCarreDoublons = {
    // avant
    -0.5f, -0.5f,  0.5f,
    0.5f, -0.5f,  0.5f,
    -0.5f,  0.5f,  0.5f,
    0.5f,  0.5f,  0.5f, 

    // arrière
    -0.5f, -0.5f, -0.5f, 
    0.5f, -0.5f, -0.5f,  
    -0.5f,  0.5f, -0.5f,  
    0.5f,  0.5f, -0.5f, 

    // gauche
    -0.5f, -0.5f, -0.5f,
    -0.5f, -0.5f,  0.5f, 
    -0.5f,  0.5f, -0.5f, 
    -0.5f,  0.5f,  0.5f, 

    // droite
    0.5f, -0.5f, -0.5f,  
    0.5f, -0.5f,  0.5f, 
    0.5f,  0.5f, -0.5f, 
    0.5f,  0.5f,  0.5f, 

    // dessous
    -0.5f, -0.5f, -0.5f, 
    0.5f, -0.5f, -0.5f, 
    -0.5f, -0.5f,  0.5f,  
    0.5f, -0.5f,  0.5f, 

    // dessus
    -0.5f,  0.5f, -0.5f, 
    0.5f,  0.5f, -0.5f, 
    -0.5f,  0.5f,  0.5f,
    0.5f,  0.5f,  0.5f,
  };
```

Puis ensuite de définir les indices des triangles de chaque face dans indices : 

```cpp
// Liste des indices des sommets de triangle pour chaque face. 
    std::vector<unsigned short> indices = {
      //avant
      0, 1, 2, 1, 2, 3,
      //arrière
      4, 5, 6, 5, 6, 7,
      //gauche
      8, 9, 10, 9, 10, 11,
      //droite
      12, 13, 14, 13, 14, 15,
      //dessous
      16, 17, 18, 17, 18, 19,
      //dessus
      20, 21, 22, 21, 22, 23
  };
```

## Coordonnées de textures

Il suffit de compléter les coordonnées de textures dans le tableau texCoords : 

```cpp
std::vector< float > texcoords = {
      //avant
      0.0f, 1.0f,
      1.0f, 1.0f,
      0.0f, 0.0f,
      1.0f, 0.0f,

      //arrière ok
      0.0f, 0.0f,
      1.0f, 0.0f,
      0.0f, 1.0f,
      1.0f, 1.0f,

      //gauche ok
      0.0f, 1.0f,
      1.0f, 1.0f,
      0.0f, 0.0f,
      1.0f, 0.0f,

      //droite ok
      0.0f, 1.0f,
      1.0f, 1.0f,
      0.0f, 0.0f,  
      1.0f, 0.0f, 

      //dessous
      0.0f, 1.0f,
      1.0f, 1.0f,
      0.0f, 0.0f,
      1.0f, 0.0f,

      //dessus
      0.0f, 1.0f,
      1.0f, 1.0f,
      0.0f, 0.0f,
      1.0f, 0.0f,
     };
```

Puis de mettre en commentaire la ligne suivante dans le shader : `frag_color =  vec4(colors, 0.5 );`

## Coordonnées de textures additionnées aux couleurs

Cette étape est très simple, il suffit de rajouter la couleur en plus de la texture dans le shader : 

```cpp
frag_color = texture( tex, texcoord ) + vec4(colors, 0.5 );
```
## Coordonnées de textures multipliées pas les couleurs

Nous avons pour cela qu'a remplacer l'addition par une multiplication : 

```cpp
frag_color = texture( tex, texcoord ) * vec4(colors, 0.5 );
```

## Changer de textures

Pour changer de textures, il suffit de changer le lien vers l'image : 

```cpp
cv::Mat img = cv::imread(  MY_RES_PATH+ (std::string )"/res/images/mur.png", cv::IMREAD_UNCHANGED );
```

## Texture procédurale

Pour afficher une texture procédurale, il faut commencer par ajouter à notre code la commande qui nous ait fournie, de l'appeler dans la fonction initTextures, et remplacer la glTexImage2D : 

```cpp
makeCheckImage();
glTexImage2D(GL_TEXTURE_2D, 0, GL_RGBA, 256, 256, 0, GL_RGBA, GL_UNSIGNED_BYTE, checkImage0);
```