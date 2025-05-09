# Trabalho de Conclusão de Curso (TCC)

Trabalho de conclusão de curso (TCC) desenvolvido para concluir o Bacharelado em Ciência da Computação na FCT-Unesp. O tema desse TCC é a comparação de métodos para identificação de imagens faciais geradas por redes neurais generativas. A principal ideia é treinar diferentes métodos que foram desenvolvidos por outros pesquisadores e fazer uma avaliação comparativa da performance deles para diferentes tipos de redes neurais generativas. Dentre esse modelos, todos utilizam abordagens diferentes para fazer a classificação das imagens. Um dos problemas notados é a dificuldade para generalização deles, o que decorre da diferença de algoritmos e métodos que diferentes modelos generativos utilizam para gerar as imagens.

## Método de Chang

Para fazer a classificação Chang utiliza um filtro SRM (camada convolucional com parâmetros não teináveis), que tem o objetivo de capturar os "defeitos" das imagens. Após aplicação do filtro SRM as imagens são passadas por uma VGG16 que classifica as imagens entre reais e falsas. Ele deu o nome para sua técnica de NA-VGG.

## Método do Cozzolino 1

O Cozzalino utiliza uma abordagem de contrastive learning para fazer a classificação das imagens. Ele utiliza uma ResNet para criar vetores de características, evitando o subsampling nas camadas iniciais. A ideia geral é utilizar uma imagem e suas versões augmentadas e treinar a rede para que sejam criadas vetores de características parecidos para essas imagens. Após esse treinamento é adicionado uma camada linear para classificar os vetores como sendo gerados por imagens reais ou falsas.


## Método do Cozzolino 2

Seguindo a mesma ideia do primeiro método proposto pelo Cozzolino, ele também vai extrair vetores de características das imagens e dessa vez utilizar um SVM para fazer essa classificação, porém as redes que ele usa se diferem da primeira. Aqui ele utiliza apenas imagens reais, passa elas pelo Blip, que vai gerar legendas para essas imagens, ele utiliza essas legendas para passar para um Stable Diffusion Model para gerar as imagens falsas, a ideia principal aqui é ter uma legenda que referencie duas imagens (falsa e real). Para a geração do vetor de características é utilizado o Clip e após ter armazenado esses vetores eles são passados para o SVM classificar a qual classe eles pertencem.

## Método de Jeong

Jeong percebeu que em muitas redes generativas acontece um defeito chamado de checkerboard ...