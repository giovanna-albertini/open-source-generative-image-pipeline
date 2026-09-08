# Open-Source Generative Image Pipeline

Pipeline de **IA Generativa para geração de imagens em ambiente local**, construído com **Stable Diffusion, Hugging Face Diffusers, PyTorch, CUDA e LoRA**.

O projeto simula um caso de uso de e-commerce para geração de criativos publicitários de acessórios para cães e explora decisões práticas de **AI Engineering** relacionadas a inferência, infraestrutura, reprodutibilidade, adaptação de modelos, privacidade, custo e licenciamento.

## Objetivo

O objetivo é avaliar como modelos open-weights podem ser utilizados para geração de imagens sem dependência de APIs externas, analisando não apenas qualidade visual, mas também requisitos reais de uma solução de produção.

O projeto busca responder perguntas como:

- Como executar um modelo generativo de imagem localmente?
- Quais recursos de GPU são necessários para inferência?
- Como tornar gerações reproduzíveis através de seeds?
- Como melhorar consistência visual utilizando LoRA?
- Quando uma arquitetura local faz mais sentido do que uma API proprietária?
- Quais riscos de licença, custo e qualidade devem ser avaliados antes de colocar esse tipo de solução em produção?

## Arquitetura

```text
Prompt / Briefing
       │
       ▼
Hugging Face Diffusers
       │
       ▼
Stable Diffusion / SD-Turbo
       │
       ▼
PyTorch + CUDA
       │
       ▼
Inferência em GPU
       │
       ├── Seed control
       ├── Prompt variations
       └── LoRA adaptation
       │
       ▼
Generated Images
       │
       ▼
Avaliação de qualidade, consistência,
licença, custo e aplicabilidade
```

## Tecnologias

- Python
- PyTorch
- CUDA
- Hugging Face Diffusers
- Transformers
- Accelerate
- Stable Diffusion / SD-Turbo
- LoRA (Low-Rank Adaptation)
- Pillow (PIL)
- Google Colab
- Hugging Face Hub

## Principais tópicos demonstrados

### Inferência local em GPU

O pipeline valida a disponibilidade de CUDA e executa o modelo em **FP16**, reduzindo o consumo de VRAM e tornando a inferência viável em GPUs mais limitadas, como uma NVIDIA T4 no Google Colab.

### Prompt Engineering

O notebook compara e estrutura briefings para geração de imagens de produto, incluindo a utilização de prompts em inglês para melhorar a aderência de modelos open-weights treinados majoritariamente com legendas nesse idioma.

### Reprodutibilidade

A utilização de **random seeds** permite controlar a aleatoriedade dos experimentos e facilita a comparação entre diferentes prompts e configurações.

### Geração de múltiplas variações

O pipeline automatiza a criação de múltiplos criativos alterando enquadramento, cenário e iluminação enquanto mantém o conceito do produto.

### LoRA

O projeto explora **Low-Rank Adaptation (LoRA)** como estratégia de adaptação eficiente de modelos para aumentar consistência de sujeito, produto ou identidade visual sem realizar fine-tuning completo.

### Avaliação arquitetural

Além da qualidade visual, o projeto discute critérios relevantes para produção:

| Critério | Avaliação |
|---|---|
| Latência | Tempo de inferência por imagem |
| VRAM | Memória necessária para executar o modelo |
| Throughput | Quantidade de imagens geradas por período |
| Reprodutibilidade | Capacidade de repetir resultados com seeds |
| Consistência | Preservação do produto ou sujeito entre gerações |
| Qualidade visual | Realismo, coerência e artefatos |
| Custo | GPU/hora versus cobrança por imagem via API |
| Privacidade | Permanência dos dados dentro da infraestrutura |
| Licença | Restrições de pesquisa, redistribuição e uso comercial |

## Open-source vs. APIs proprietárias

Uma arquitetura local pode ser especialmente interessante quando existem requisitos de:

- privacidade e execução on-premises;
- alto volume de geração;
- personalização com LoRA, ControlNet ou técnicas similares;
- maior controle sobre o pipeline de inferência.

Por outro lado, APIs proprietárias tendem a reduzir complexidade operacional e podem apresentar melhor desempenho em tarefas como geração de texto legível dentro das imagens.

A conclusão do projeto é que **não existe um único melhor modelo para todos os cenários**: a decisão depende das restrições de qualidade, custo, infraestrutura, privacidade e licença.

## Estrutura do repositório

```text
open-source-generative-image-pipeline/
│
├── notebooks/
│   └── open_source_generative_image_pipeline.ipynb
│
├── .gitignore
└── README.md
```

## Como executar

O notebook foi preparado para execução em ambiente com GPU CUDA, como o Google Colab.

1. Abra o notebook no Google Colab.
2. Acesse **Ambiente de execução → Alterar tipo de ambiente de execução**.
3. Selecione uma GPU disponível.
4. Execute as células em sequência.
5. Na primeira execução, os pesos do modelo serão baixados do Hugging Face Hub.

> O notebook utiliza versões de bibliotecas testadas no projeto. Dependendo da data de execução, pode ser necessário atualizar os pinos de versão.

## Modelo utilizado

O experimento principal utiliza:

```text
stabilityai/sd-turbo
```

O SD-Turbo foi escolhido por permitir inferência rápida e execução em GPUs relativamente limitadas.

**Importante:** a licença do modelo deve ser validada antes de qualquer utilização comercial. O notebook trata explicitamente esse ponto e compara alternativas mais adequadas a cenários de produção.

## Limitações observadas

- dificuldade de modelos leves em gerar texto e logotipos corretamente;
- variação na aparência do produto entre diferentes gerações;
- dependência de GPU e VRAM;
- manutenção de drivers, bibliotecas e pesos em arquiteturas locais;
- necessidade de validação de licença de cada modelo e adaptação utilizada.

Como mitigação, o projeto considera curadoria humana, imagens reais de referência, seeds padronizadas e técnicas como **LoRA, ControlNet, IP-Adapter e inpainting**.

## Próximas evoluções

- ControlNet para maior controle estrutural;
- inpainting para edição localizada;
- comparação com SDXL e FLUX;
- benchmark automático de latência e VRAM;
- rastreamento estruturado de experimentos;
- API de inferência com FastAPI;
- containerização com Docker;
- deploy em infraestrutura GPU;
- observabilidade e monitoramento de custo por geração.

## Competências demonstradas

`Generative AI` · `AI Engineering` · `Diffusion Models` · `Stable Diffusion` · `LoRA` · `PyTorch` · `CUDA` · `Hugging Face` · `Prompt Engineering` · `Model Inference` · `Open-Weights Models` · `GPU Computing`