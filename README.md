# Big Data: Análise Comparativa entre MySQL e Neo4j

## 📋 Sobre o Projeto

Este projeto apresenta uma análise comparativa de desempenho entre um Sistema Gerenciador de Banco de Dados Relacional (MySQL) e um Sistema NoSQL especializado em grafos (Neo4j), utilizando um dataset de Big Data com características de rede social.

## 🎯 Objetivo

Avaliar e demonstrar as diferenças, aplicações e limitações dos sistemas Relacionais em comparação com sistemas Não-Relacionais no contexto do gerenciamento e manipulação de Big Data orientado a relacionamentos.

## 🔍 Problema Investigado

O estudo investiga:

- **Capacidade de Modelagem**: Comparação entre a representação de um grafo social em modelo tabular (MySQL) versus modelo de grafo (Neo4j)
- **Eficiência Operacional**: Análise de desempenho em três categorias de consultas:
  - Consultas de Agregação
  - Consultas de Texto
  - Consultas de Relação (travessia de grafo)

## 🛠️ Tecnologias Utilizadas

### MySQL
- SGBD Relacional tradicional
- Modelagem em Terceira Forma Normal (3NF)
- Índices B-Tree otimizados

### Neo4j
- SGBD NoSQL de Grafos
- Modelo de Grafo de Propriedades (Property Graph Model)
- Navegação nativa de relacionamentos

## 📊 Dataset

**MUSAE GitHub Social Network** (Kaggle)

| Arquivo | Descrição | Volume |
|---------|-----------|--------|
| `musae_git_target.csv` | Nós (usuários do GitHub) com metadados | ~37.700 registros |
| `musae_git_edges.csv` | Arestas (conexões entre usuários) | ~290.000 registros |
| `musae_git_features.csv` | Atributos/Features dos usuários | ~2.5 Milhões registros |

## 🏗️ Arquitetura

### Modelagem Neo4j (Grafo de Propriedades)

```
(:User)-[:FOLLOWS]->(:User)
```

- **Nós**: Representam usuários com propriedades
- **Relações**: Conexões diretas entre usuários
- **Complexidade**: O(1) para vizinhos de 1º grau, O(N) para N-graus

### Modelagem MySQL (Relacional)

- **nodes_target**: Tabela principal de usuários
- **edges**: Tabela de relacionamentos
- **features**: Tabela N:M para atributos
- **Complexidade**: O(n^k) com múltiplos JOINs

## 🎯 Objetivos Específicos

1. **Modelagem e Carga de Dados**: Implementar e carregar o dataset em ambos os sistemas
2. **Execução de Consultas**: Desenvolver consultas estratégicas em ambas as plataformas
3. **Análise de Desempenho**: Medir tempo de execução e uso de recursos
4. **Conclusões**: Comprovar vantagens do Neo4j em operações de grafo complexas

## 💡 Casos de Uso - Vantagens do Neo4j

| Aplicação | Problema Resolvido | Vantagem |
|-----------|-------------------|----------|
| **Redes Sociais** | Encontrar "amigos de amigos" | Navegação profunda instantânea vs múltiplos JOINs |
| **Detecção de Fraudes** | Identificar anéis de fraude | Busca eficiente de padrões e loops |
| **Gerenciamento de Identidade** | Mapear hierarquias complexas | Processa M:N sem limitação de profundidade |

## 📈 Resultados Esperados

O Neo4j demonstra superioridade significativa em:

- **Consultas de Travessia**: Vizinhos de 2º grau e caminho mais curto
- **Performance**: Ordens de magnitude mais rápido em relações complexas
- **Escalabilidade**: Desempenho linear (O(N)) vs exponencial (O(n^k)) do MySQL

### Ponto de Inflexão

Em consultas com profundidade > 2 graus, o Neo4j mantém desempenho constante enquanto o MySQL degrada exponencialmente.

## 🚀 Como Executar

```bash
# Clone o repositório
git clone [url-do-repositorio]

# Importe os dados no MySQL
mysql -u root -p < mysql_schema.sql

# Importe os dados no Neo4j
# [instruções específicas de importação]

# Execute as consultas comparativas
# [scripts de teste]
```

## 📝 Conclusão

Este estudo fornece base técnica para escolha da tecnologia adequada em projetos de Big Data orientados a relacionamentos, demonstrando que o Neo4j é indiscutivelmente superior ao MySQL quando a relação entre os dados é o foco principal da análise.

## 👥 Autores

[Seus nomes aqui]

## 📄 Licença

[Tipo de licença]

---

**Nota**: Este é um projeto acadêmico com fins educacionais e de pesquisa.
