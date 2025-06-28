# AED Challenge - Hackathon DataCentric AI

Este repositório contém o notebook desenvolvido durante o hackathon da disciplina **DataCentric AI**, oferecida pelo Instituto Metrópole Digital da UFRN e ministrada pelo professor Dr. Elias Jacob de Menezes Neto.

## 👥 Equipe

* Allyson Santos  
* Dimitri Amaral de Lima

## 🎯 Objetivo

Construir um método automatizado para identificar imagens com rótulos incorretos no dataset de treinamento. A avaliação foi baseada na quantidade de erros corretamente identificados.

## 📁 Datasets

Fornecidos pela organização do hackathon:

* **`training_set`**  
  Contém imagens e rótulos. Possui rótulos incorretos, mas sem ground truth disponível.

* **`validation_set`**  
  Contém imagens, rótulos e a coluna `is_noisy`, que informa se o rótulo está errado (`1`) ou correto (`0`). Usado para desenvolvimento e validação do método.

Fonte original: Hackathon organizado por Andrew Ng e a equipe do Deeplearning.ai.

## 🧪 Estratégia

Nossa abordagem foi baseada em embeddings visuais e detecção de ruído com Cleanlab. Etapas:

1. **Carregamento dos dados:** leitura do dataset com as imagens representadas por pixels.  
2. **Geração das imagens PNG:** a partir dos pixels, criamos arquivos de imagem png.  
3. **Geração de embeddings:** extração de representações vetoriais das imagens com modelos da Hugging Face.  
4. **Identificação de duplicatas e outliers:** análise dos embeddings usando Cleanlab para detectar imagens semelhantes e potenciais anomalias.  
5. **Detecção de erros de rótulo:** aplicação do Cleanlab para identificar possíveis rótulos incorretos, treinando classificadores e avaliando seu desempenho com a `validation_set`.  
6. **Predição dos erros no `training_set`:** geração do arquivo final `submission.csv` com as predições.

## 📦 Requisitos

As bibliotecas utilizadas neste projeto incluem:

| Biblioteca     | Finalidade                                         |
| -------------- | -------------------------------------------------- |
| `pandas`       | Manipulação de dados tabulares                     |
| `requests`     | Requisições HTTP para download de imagens/dados    |
| `Pillow`       | Leitura e processamento de imagens                 |
| `matplotlib`   | Visualização de dados                              |
| `numpy`        | Cálculo numérico                                   |
| `transformers` | Extração de embeddings com modelos pré-treinados   |
| `tqdm`         | Barras de progresso                                |
| `joblib`       | Serialização de modelos e dados                    |
| `cleanlab`     | Detecção de erros de rótulo e dados ruidosos       |
| `scikit-learn` | Modelos de ML e métricas (ex: regressão logística) |
| `xgboost`      | Classificador com boosting                         |

Para instalar todas as dependências, execute:

```bash
pip install -r requirements.txt
```

## ▶️ Como Executar

1. Clone este repositório:

   ```bash
   git clone https://github.com/css-allyson/hackathon-the-AED-challenge.git
   cd hackathon-the-AED-challenge
   ```

2. Abra e execute o notebook `hackaton.ipynb`.

3. Ao final, será gerado o arquivo `submission.csv` com as seguintes colunas:

| uid            | is\_noisy |
| -------------- | --------- |
| d58ccd8d-65b1-4f7d-914b-50ce98c1bbeb | 1         |
| e04c4f02-0a19-4020-a028-e2ed56d2f081 | 0         |

## 🚀 Submissão

* Arquivo final: `submission.csv`
* Formato: duas colunas — `uid` (identificador da imagem) e `is_noisy` (1 = rótulo incorreto, 0 = correto).
* Upload no sistema de correção automática e repositório GitHub com notebook + README.


## 📄 Licença

Projeto acadêmico para fins educacionais. Livre para uso não comercial.
