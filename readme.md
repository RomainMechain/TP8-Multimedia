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