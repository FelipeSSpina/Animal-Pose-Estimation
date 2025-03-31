# Detecção de Emoções com Base em Keypoints Faciais

Este repositório contém um projeto que desenvolvi para detectar expressões faciais (Alegre, Neutro e Raiva) utilizando a extração dos keypoints do rosto com o MediaPipe Face Mesh.

## Descrição do Projeto

Eu desenvolvi uma abordagem em que:

1. **Extração dos Keypoints:**  
   Eu utilizei o MediaPipe Face Mesh para identificar os pontos de referência do meu rosto em imagens armazenadas no Google Drive. Os pontos 33 e 263, que representam os cantos externos dos olhos, são usados para calcular a distância interocular – meu referencial para normalização.

2. **Cálculo das Métricas:**  
   - **Boca:** Calculei a abertura da boca a partir da diferença entre os keypoints 13 (lábio superior) e 14 (lábio inferior) e dividi esse valor pela distância interocular para obter a razão da boca.  
   - **Bochecha:** Comparei os pontos da bochecha (159 e 205 no lado esquerdo; 386 e 425 no lado direito) para determinar a razão da bochecha.  
   - **Sobrancelhas:** Medindo a distância entre as sobrancelhas internas (keypoints 55 e 285) e normalizando pela distância interocular, eu pude identificar expressões de raiva, nas quais as sobrancelhas se aproximam.

3. **Visualização:**  
   Para facilitar a comparação, eu usei um gráfico de radar, onde as razões são escalonadas (multiplicadas por 100), permitindo que diferenças sutis fiquem evidentes.

4. **Classificação das Expressões:**  
   Baseado em limiares empíricos que defini, classifiquei as expressões em:
   - **ALEGRE:** Quando a razão da boca ultrapassa um determinado limiar.
   - **RAIVA:** Quando a razão entre as sobrancelhas indica que elas estão muito próximas.
   - **NEUTRO:** Quando as medições não indicam nenhuma das duas condições anteriores.

## Como Executar

1. **Configuração:**  
   - Faça o upload das imagens de rosto (por exemplo, `meu_rosto.jpg`, `meu_rosto2.jpg` e `meu_rosto3.jpg`) no seu Google Drive.
   - Altere os caminhos das imagens no notebook conforme necessário.

2. **Execução:**  
   - Abra o notebook no Google Colab.
   - Execute as células na ordem apresentada.
   - Visualize os resultados: as imagens anotadas, o gráfico de radar e a classificação final das expressões.

## Considerações Finais

Eu demonstrei que é possível implementar um sistema de detecção de emoções com baixo custo computacional utilizando medições simples dos keypoints faciais. Essa abordagem pode ser facilmente ajustada para se adaptar a diferentes condições de iluminação, ângulos e expressões, bastando calibrar os limiares empíricos.

Sinta-se à vontade para explorar, ajustar e aprimorar o código conforme suas necessidades!

Este é o [link](https://colab.research.google.com/drive/1eMfmlZa_VKp-Fg4TSeDVVzIWTILq0Eq3?usp=sharing) do Colab original com o códgio implementado!
