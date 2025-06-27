# Sistema NCA-SEM

Sistema web completo para análise NCA-SEM (Necessary Condition Analysis - Structural Equation Modeling) implementado com FastAPI (backend) e React (frontend).

## Funcionalidades

### Análises Disponíveis
- **SEM (Structural Equation Modeling)**: Análise de suficiência que identifica fatores que contribuem em média para o resultado
- **NCA (Necessary Condition Analysis)**: Análise de necessidade que identifica condições indispensáveis para o resultado
- **NCA-SEM Integrado**: Análise combinada que oferece uma visão completa das relações causais

### Características Técnicas
- Upload de dados CSV
- Interface web intuitiva
- Visualização de resultados
- Exportação de relatórios
- API REST documentada (Swagger/OpenAPI)

## Estrutura do Projeto

```
nca-sem-system/
├── backend/                 # API FastAPI
│   ├── main.py             # Aplicação principal
│   ├── models.py           # Modelos Pydantic
│   ├── sem_analysis.py     # Módulo de análise SEM
│   ├── nca_analysis.py     # Módulo de análise NCA
│   └── venv/               # Ambiente virtual Python
├── frontend/               # Aplicação React
│   ├── src/
│   │   ├── components/     # Componentes React
│   │   ├── App.jsx         # Componente principal
│   │   └── App.css         # Estilos
│   └── package.json
└── sample_data.csv         # Dados de exemplo
```

## Como Executar

### Backend (FastAPI)
```bash
cd backend
source venv/bin/activate
python main.py
```
O backend estará disponível em: http://localhost:8000
Documentação da API: http://localhost:8000/docs

### Frontend (React)
```bash
cd frontend
npm run dev
```
O frontend estará disponível em: http://localhost:5173

## Uso do Sistema

### 1. Upload de Dados
- Acesse a aba "Upload de Dados"
- Faça upload de um arquivo CSV com suas variáveis observadas
- O sistema mostrará uma prévia dos dados carregados

### 2. Análise SEM
- Configure as variáveis latentes e seus indicadores
- Defina os caminhos estruturais entre as variáveis
- Execute a análise para obter índices de ajuste e coeficientes

### 3. Análise NCA
- Selecione as variáveis de condição e resultado
- Escolha a técnica de ceiling line (CR-FDH ou CE-FDH)
- Execute a análise para obter effect sizes e tabelas de bottleneck

### 4. Análise Integrada NCA-SEM
- Configure tanto o modelo SEM quanto as condições NCA
- Execute a análise combinada para insights complementares
- Obtenha fatores de suficiência e necessidade

### 5. Visualização de Resultados
- Acesse a aba "Resultados" para ver os últimos resultados
- Exporte dados em JSON ou relatórios em texto
- Analise métricas e interpretações

## Metodologia NCA-SEM

O sistema implementa a metodologia integrada NCA-SEM conforme descrita na literatura acadêmica:

1. **Primeiro**: Executa análise SEM para validar o modelo de medida e calcular scores das variáveis latentes
2. **Segundo**: Utiliza os scores latentes na análise NCA para identificar condições necessárias
3. **Resultado**: Combina lógicas de suficiência (SEM) e necessidade (NCA) para uma compreensão completa

### Interpretação dos Resultados

#### SEM (Suficiência)
- **CFI/TLI > 0.95**: Bom ajuste do modelo
- **RMSEA < 0.06**: Bom ajuste
- **Coeficientes significativos**: Relações de suficiência

#### NCA (Necessidade)
- **Effect Size (d)**:
  - 0 < d < 0.1: Efeito pequeno
  - 0.1 ≤ d < 0.3: Efeito médio  
  - 0.3 ≤ d < 0.5: Efeito grande
  - d ≥ 0.5: Efeito muito grande
- **p < 0.05**: Estatisticamente significativo
- **Tabela de Bottleneck**: Níveis mínimos necessários

## Tecnologias Utilizadas

### Backend
- FastAPI (framework web)
- Pydantic (validação de dados)
- NumPy/Pandas (processamento de dados)
- SciPy (análises estatísticas)
- Scikit-learn (análise fatorial)

### Frontend
- React 18 (interface)
- Vite (build tool)
- Axios (requisições HTTP)
- Recharts (visualizações)
- Lucide React (ícones)

## Dados de Exemplo

O arquivo `sample_data.csv` contém dados simulados com 8 variáveis (x1-x3, y1-y3, z1-z2) que podem ser usados para testar o sistema.

## API Endpoints

- `POST /upload-data`: Upload de arquivo CSV
- `POST /analyze-sem`: Executar análise SEM
- `POST /analyze-nca`: Executar análise NCA  
- `POST /analyze-nca-sem`: Executar análise integrada
- `GET /data/{data_id}`: Obter informações dos dados

## Considerações Técnicas

- O sistema utiliza implementações simplificadas das análises para fins demonstrativos
- Em produção, recomenda-se integração com bibliotecas especializadas (lavaan, semopy)
- Os dados são armazenados em memória (para produção, usar banco de dados)
- CORS está habilitado para desenvolvimento

## Próximos Passos

1. Integração com bibliotecas estatísticas mais robustas
2. Implementação de visualizações gráficas (scatter plots, path diagrams)
3. Suporte a diferentes formatos de dados
4. Sistema de autenticação e persistência de dados
5. Testes automatizados e validação de modelos
