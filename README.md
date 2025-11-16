# Atividade CIFAR-100
📊 ANÁLISE DOS RESULTADOS - CIFAR-100


## Observações sobre o Treinamento com CIFAR-100:

A LeNet-5 adaptada para CIFAR-100 (com in_channels=3 e 100 classes de saída) foi treinada por
24 épocas, demonstrando progressão consistente mas limitada devido à complexidade do dataset.

*Resultados Alcançados:*
- Acurácia inicial (Epoch 1): Train 3.57% | Test 4.68%
- Acurácia final (Epoch 24): Train 25.48% | Test *23.46%*
- Loss final: Train 3.0806 | Test 3.2118
- Progressão total: ganho de ~20% em acurácia ao longo de 24 épocas

Essa acurácia de 23.46% é condizente com o esperado para a arquitetura LeNet-5 aplicada ao
CIFAR-100. O dataset CIFAR-100 é significativamente mais desafiador que o CIFAR-10 (que atinge
65-70% com LeNet-5), devido ao número 10x maior de classes (100 vs 10).

As curvas de loss e accuracy revelam:
- *Convergência gradual*: redução consistente do loss ao longo das épocas
- *Overfitting moderado*: pequena diferença entre train loss (3.08) e test loss (3.21)
- *Aprendizado contínuo*: acurácia de teste ainda estava melhorando na época 24
- *Limitação arquitetural*: LeNet-5 tem apenas 69,656 parâmetros, insuficientes para
  capturar toda a complexidade de 100 classes distintas

## Análise dos Feature Maps:

A visualização dos feature maps revela o processamento hierárquico da informação:

- *conv1 + relu1*: Os 6 filtros da primeira camada (28x28) detectam características de baixo
  nível como bordas horizontais, verticais, diagonais e gradientes de cor. Com 100 classes,
  a rede precisa identificar detalhes sutis que diferenciam categorias similares.

- *pool1*: O max pooling (2x2) reduz de 28x28 para 14x14, mantendo as características mais
  salientes e criando invariância posicional parcial, essencial para robustez.

- *conv2 + relu2*: Os 16 filtros da segunda camada (10x10) combinam features de conv1 para
  detectar padrões mais complexos e abstratos. Observa-se ativação seletiva para estruturas
  específicas das imagens.

- *pool2*: Segunda redução dimensional (14x14 -> 5x5), consolidando representações abstratas
  antes do classificador.

A visualização confirma que a LeNet-5, embora simples, consegue extrair features relevantes.
Porém, para 100 classes, arquiteturas mais profundas (VGG, ResNet, EfficientNet) seriam mais
adequadas, pois oferecem maior capacidade de representação (milhões de parâmetros vs 69k).

## Comparação e Contexto:

- *CIFAR-10 com LeNet-5*: ~65-70% de acurácia (esperado)
- *CIFAR-100 com LeNet-5*: ~23.46% de acurácia (nosso resultado)
- *CIFAR-100 com ResNet-18*: ~75-80% de acurácia (benchmark comum)
- *CIFAR-100 State-of-the-art*: >95% de acurácia (redes modernas)

A diferença de 3x na dificuldade (70% -> 23%) ao aumentar de 10 para 100 classes demonstra
o desafio de classificação granular com arquiteturas simples.

## Conclusão:

O experimento demonstrou com sucesso:

✅ Implementação de CNN (LeNet-5) adaptada para CIFAR-100

✅ Treinamento completo de 24 épocas com registro de métricas

✅ Implementação de hooks para captura de ativações intermediárias

✅ Visualização de feature maps de todas as 6 camadas

✅ Análise quantitativa e qualitativa dos resultados

Os resultados confirmam que a complexidade do CIFAR-100 (100 classes) exige arquiteturas mais
sofisticadas para atingir acurácias superiores a 70-80%. A LeNet-5, com sua simplicidade,
atingiu 23.46% - um resultado razoável considerando suas limitações arquiteturais.


✅ ATIVIDADE CONCLUÍDA - TODOS OS REQUISITOS ATENDIDOS
