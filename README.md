# Azure Cognitive Search

O Azure Cognitive Search é um serviço de busca em nuvem empresarial que combina poderosos recursos de indexação com capacidades de IA para transformar dados em insights acionáveis. Diferente de mecanismos de busca convencionais, ele entende o contexto e o significado por trás dos dados, oferecendo resultados relevantes mesmo em consultas complexas.

### Fontes Suportadas
| Fonte | Descrição | Casos de Uso |
|-------|-----------|--------------|
| **Azure Blob Storage** | Armazena arquivos diversos (PDF, Word, etc.) | Documentação digital |
| **Data Lake Gen2** | Armazena big data em hierarquia | Análise de dados |
| **Azure Table Storage** | Dados semi-estruturados em tabelas | Logs transacionais |

## 1. Ingestão de Dados

A primeira etapa no Azure Cognitive Search é a ingestão de dados, onde fontes de dados são conectadas para indexação.

### Fontes de Dados Suportadas

**Azure Blob Storage**  
- Armazena arquivos como JSON, CSV, PDF, Word, Excel e etc.  
- Pode ser configurado para indexação automática de novos arquivos quando são adicionados.

**Azure Data Lake Storage Gen2**  
- Ideal para big data e análises avançadas.  
- Permite indexação hierárquica de pastas e arquivos.

**Azure Table Storage**  
- Armazena dados semi-estruturados em formato de tabela.  
- Útil para dados transacionais e logs.

### Processo de Ingestão

**Defina um Indexador**  
- Configura a conexão com a fonte de dados.  
- Define a frequência de atualização.

**Mapeamento de Campos**  
- Especifica quais colunas/atributos serão indexados.

**Pré-processamento Opcional**  
- Decodificação de arquivos (ex.: extrair texto de PDFs).

---

## 2. Enriquecimento de IA

O enriquecimento de IA aplica habilidades cognitivas para extrair informações valiosas de dados brutos.

### Conjuntos de Habilidades

Um skillset define um pipeline de processamento que pode incluir:
- **Reconhecimento de Entidades**  
  Identifica pessoas, organizações, locais e datas no texto.
- **Tradução de Texto**  
  Converte conteúdo para outros idiomas (ex.: inglês → português).
- **Análise de Sentimento**  
  Classifica o tom do texto (positivo, neutro, negativo).
- **OCR**  
  Extrai texto de imagens e PDFs digitalizados.
- **Detecção de Tópicos*  
  Identifica conceitos relevantes em documentos longos.

### Como Funciona?

1. Documentos são processados pelo skillset.  
2. Cada habilidade adiciona metadados ao documento.  
3. Dados enriquecidos são serializados em JSON.  
   - Estrutura compatível com o mecanismo de busca.  
4. Indexação otimizada para pesquisa.  
   - Os metadados permitem buscas avançadas (ex.: "encontrar todos os documentos com menção a 'Microsoft' e sentimento positivo").
---

## 3. Indexação e Pesquisa

O índice de busca armazena os dados processados para consultas rápidas.

### Componentes Principais

- **Campos Pesquisáveis**  
  Texto processado e tokens para buscas full-text.

- **Campos Filtráveis**  
  Permitem refinamento (ex.: filtrar por data, categoria).

- **Campos Classificáveis**  
  Ordenação por relevância, data, etc.

- **Sugestores (Auto-complete)**  
  Previsão de termos durante a digitação.

### Tipos de Consulta

### Tipos de Consulta

- **Busca Simples**  
  `search=Azure` (retorna documentos com a palavra "Azure").

- **Busca Semântica**  
  Usa IA para entender a intenção (ex.: "Como migrar para a nuvem?" retorna guias de migração).

- **Filtros**  
  `$filter=date ge 2023-01-01` (apenas documentos após 2023).  
  -> Observação: Embora poderosa, a utilização de filtros ainda não é muito usual para muitos usuários, exigindo conhecimento sobre a sintaxe e estrutura dos dados.
---

## 4. Explorando os Resultados

Depois da indexação, os dados podem ser consultados e visualizados em aplicações.

### Integração em Aplicativos

- **APIs REST**  
  Consultas HTTP diretamente para o serviço de busca.

- **SDKs (C#, Python, Java, javaScript)**  
  Facilita a integração em apps web/mobile.

- **Power BI**  
  Conecta ao índice para dashboards analíticos muito usado nas empresas.
 
### Visualizações

- **Gráficos de Frequência**  
  Mostra termos mais recorrentes.

- **Mapas de Calor**  
  Destaque de tópicos relevantes.

- **Facetas Navegáveis**  
  Filtros interativos (ex.: "Mostrar apenas artigos técnicos").

---

## 5. Casos de Uso Comuns

- **E-commerce**  
  Busca por produtos com filtros por cor, preço e avaliações.

- **Documentação Técnica**  
  Pesquisa semântica em manuais e FAQs.

- **Análise de Mídia Social**  
  Identificação de tendências e sentimentos em posts.
