Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Fringilla phasellus faucibus scelerisque eleifend donec pretium vulputate. Volutpat maecenas volutpat blandit aliquam etiam erat. Lorem mollis aliquam ut porttitor. Proin libero nunc consequat interdum varius sit amet mattis vulputate. Faucibus a pellentesque sit amet porttitor eget dolor. Scelerisque varius morbi enim nunc.

Erat imperdiet sed euismod nisi porta. Imperdiet nulla malesuada pellentesque elit eget gravida cum. Velit dignissim sodales ut eu sem integer vitae justo. 

#Pasos de la Parte3
1. Descargamos el proyecto https://bitbucket.org/orbisunt/orbis-example-training
2. Creamos repositoroi en github con nombre orbis-example-training
3. Enlazamos con el repositorio remote con las intruccion: git remote add origin git@github.com:joantasayco/orbis-example-training.git
4. Se sube los cambios al repositorio: 
    git add .
    git commit -m 'feat training: Subiendo archvos'
    git push origin master
5. Identificamos el archivo pesado
    git gc
    git verify-pack -v .git/objects/pack/pack-191fe08511297bcf8d15bbbfe6df0f7506eebc22.idx
    git rev-list --objects
    git rev-list --objects --all | grep 2ce5eca830c1f68c365b5323677e7c37212eccf6
    git rm -d 1_tSyuv3ZRCfsSD5aXB7v8DQ.png
    git add .
    git commit -m 'fix png: Se elimina archivo pesado'
    git push origin master

# Parte 7

## .5 Usando docker run ejecutar npm install
1. Que pasas sino no especifico workdir: el npm install no puede ejecutar el archivo package.json
2. Comando que se uso: docker run --name Mikhael -v "D:\Angello\Proyectos\orbis-example-training":/App -w /App -it angello/orbis-training-docker:1.5.0