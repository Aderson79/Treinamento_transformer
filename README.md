Laboratório 05: Treinamento Fim-a-Fim do Transformer

Este repositório contém a conclusão da Unidade I, focada na implementação, integração e treinamento de uma arquitetura Transformer para tradução de texto (Inglês -> Alemão), utilizando o dataset multi30k.

🚀 Visão Geral do Projeto

O objetivo deste laboratório foi evoluir os componentes matemáticos isolados desenvolvidos no Laboratório 04 para um pipeline de treinamento completo e funcional.

Diferente dos laboratórios anteriores, onde os pesos eram estáticos ou gerados aleatoriamente via NumPy para teste, aqui o modelo aprende através de Backpropagation e do otimizador Adam.

🛠️ Mudanças e Adaptações (Lab 04 -> Lab 05)

Para cumprir os requisitos de treinamento, foram necessárias as seguintes adaptações:

Migração para PyTorch: As funções originais em NumPy foram refatoradas para classes que herdam de torch.nn.Module. Isso foi indispensável para permitir o cálculo automático de gradientes (autograd) e o uso de GPU.

Gerenciamento de Pesos: O sistema de _weight_cache (dicionários manuais de pesos) do Lab 04 foi substituído por camadas nn.Linear e nn.Embedding.

Máscara de Atenção Causal: A lógica de máscara de "olhar para frente" (Look-ahead mask) foi integrada ao Forward Pass do Decoder para garantir que o modelo não tenha acesso a tokens futuros durante o treino.

Loop Auto-regressivo: A lógica de inferência foi adaptada para gerar traduções token a token após o treinamento.

🤖 Créditos e Ferramentas de IA

Seguindo as diretrizes do contrato pedagógico:

Preparação de Dados e Tokenização: Foi utilizada Inteligência Artificial (Gemini/ChatGPT) para auxiliar na integração com a biblioteca datasets do Hugging Face e na configuração do AutoTokenizer (modelo bert-base-multilingual-cased). Isso permitiu agilizar a transformação de texto bruto em tensores compatíveis com o modelo.

Adaptação Pytorch: IA foi utilizada como suporte consultivo para converter as operações de matrizes do NumPy para as operações equivalentes em tensores do PyTorch, garantindo a integridade do fluxo dos gradientes.

📋 Requisitos de Sistema

Para rodar este laboratório, você precisará de:

Python 3.8 ou superior.

Bibliotecas listadas abaixo (instale via terminal):

pip install torch datasets transformers numpy


🏃 Como Rodar o Laboratório

Clone o repositório e garanta que todos os arquivos .py estejam na mesma pasta.

Execute o script principal:

python inferencia.py


O que esperar:

O script baixará automaticamente o dataset multi30k e o tokenizador.

Iniciará um treinamento de 20 épocas em um subconjunto de 1000 frases.

Você verá o valor da Loss (perda) cair a cada época, indicando convergência.

Ao final, o modelo tentará "vomitar" (traduzir por memorização) uma frase do conjunto de treino para provar a integridade estrutural.
