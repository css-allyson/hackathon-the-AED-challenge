Perfeito! Aqui está o `README.md` completo, já incorporando as dependências em formato Markdown:
#  AED Challenge - Hackathon DataCentric AI

Este repositório contém o notebook desenvolvido durante o hackathon da disciplina *DataCentric AI*, com foco em detecção de erros de anotação (Annotation Error Detection - AED) em datasets de aprendizado de máquina.

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

1. **Carregamento das imagens** e leitura dos metadados.
2. **Geração de embeddings** com modelos da Hugging Face (`AutoImageProcessor`, `AutoModel`).
3. **Identificação de duplicatas e outliers** nos embeddings com Cleanlab.
4. **Uso do Cleanlab para detectar possíveis erros de rótulo**, treinando classificadores e avaliando sua performance com a `validation_set`.
5. **Predição dos erros no `training_set`** e geração do arquivo final `submission.csv`.

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

Para instalar todas as dependências:

```bash
pip install pandas requests Pillow matplotlib numpy transformers tqdm joblib cleanlab scikit-learn xgboost
```

## ▶️ Como Executar

1. Clone este repositório:

   ```bash
   git clone https://github.com/seu-usuario/nome-do-repositorio.git
   cd nome-do-repositorio
   ```

2. Abra e execute o notebook `aed_hackathon_notebook.ipynb`.

3. Ao final, será gerado o arquivo `submission.csv` com as seguintes colunas:

| uid            | is\_noisy |
| -------------- | --------- |
| image\_001.png | 1         |
| image\_002.png | 0         |

## 🚀 Submissão

* Arquivo final: `submission.csv`
* Formato: duas colunas — `uid` (identificador da imagem) e `is_noisy` (1 = rótulo incorreto, 0 = correto).
* Upload no sistema de correção automática e repositório GitHub com notebook + README.

## 📅 Cronograma

* Início: **26/06/2025 - 19h00**
* Término: **26/06/2025 - 21h30**
* Prazo SIGAA: **27/06/2025 - 23h59**

## 📄 Licença

Projeto acadêmico para fins educacionais. Livre para uso não comercial.
