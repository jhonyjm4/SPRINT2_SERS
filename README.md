# ChargeGrid Intelligence (CGI) - Resilient Energy Hub
## Sprint 2 - Prova de Conceito Funcional e Gestão de Projeto
### Equipe 4 - 1CCPG

**Integrantes:**
* João Marcelo — RM: 572569
* Lucas Barreto — RM: 573149
* Pablo Renato — RM: 569894
* Pedro Vianna — RM: 570747

---

## 📋 Descrição do Projeto e Evolução (Sprint 1 vs. Sprint 2)

Na **Sprint 1**, a nossa equipe mapeou os desafios críticos na transição dos carregadores da GoodWe do ecossistema residencial para o comercial compartilhado. Identificamos gargalos severos de infraestrutura, tais como: **risco iminente de sobrecarga na rede local**, **falta de interoperabilidade de protocolos** e **inviabilidade econômica** devido à dependência de tarifas dinâmicas das concessionárias.

Nesta **Sprint 2**, evoluímos a abordagem teórica para uma **Prova de Conceito Funcional Digital**. Desenvolvemos um algoritmo em Python (Google Colab) que atua como o firmware inteligente do **Inversor Híbrido GoodWe (Linha ET)** integrado a um **Smart Meter**. O sistema analisa em tempo real variáveis oscilatórias do ambiente e executa o **Controle Dinâmico de Carga** para proteger a rede elétrica, orquestrar fontes renováveis e alimentar o assistente de IA **ChargeOps** com tomada de decisão baseada na técnica *Chain of Thoughts*.

---

## 🛠️ Arquitetura e Fluxo do Sistema

O ecossistema do eletroposto inteligente funciona seguindo as seguintes camadas de integração:

1. **Camada de Captura (IoT & Sensores):** O *Smart Meter* comercial mede constantemente a demanda do prédio comercial, enquanto os sensores de irradiação medem a potência gerada pelos painéis fotovoltaicos locais.
2. **Camada de Processamento (CGI Edge Core):** O Inversor Híbrido GoodWe compila as métricas de entrada de forma contínua. Caso a soma do consumo comercial com a demanda dos carregadores ultrapasse a capacidade contratada da concessionária, o algoritmo de **Balanço Dinâmico de Carga** entra em ação.
3. **Camada de Atuação (Smart Chargin HCA):** O sistema reconfigura a modulação dos carregadores rápidos HCA, reduzindo temporariamente a corrente (kW) de forma equilibrada entre os carros para evitar quedas no disjuntor.
4. **Camada de Relatórios (Plataforma SEMS):** Todos os logs gerados são enviados via barramento de dados para a plataforma SEMS, gerando transparência tarifária e histórico de eficiência.
5. **Camada de Atendimento (IA Chatbot):** O assistente **ChargeOps** monitora a telemetria do inversor para responder aos usuários humanos usando lógica de raciocínio lógico em cadeia (*Chain of Thoughts*).

### Fluxograma Lógico de Tomada de Decisão:
```text
[Sensores IoT / Smart Meter] 
        │
        ▼
[Leitura dos Dados Randômicos: Solar, Comercial, Veículos]
        │
        ▼
Calcula Potência Disponível no Hub = (Limite Concessionária + Solar) - Consumo Predial
        │
        ├─► [Demanda Solicitada <= Potência Disponível] ──► Status: Operação Normal (Carga Máxima)
        │
        └─► [Demanda Solicitada > Potência Disponível]  ──► Status: Contrapartida Ativa (Modulação Inteligente)
        │
        ▼
[Envio de Telemetria p/ Plataforma SEMS] ──► [Alimentação Contextual do Chatbot ChargeOps]
⚡ Princípios de Energias Renováveis e Sustentabilidade (SERS)
A solução fundamenta-se na orquestração de um futuro sustentável através de três pilares práticos:

Microgeração Distribuída e Armazenamento (Baterias): Ao integrar geração solar local, o ecossistema alivia o estresse da rede de transmissão da concessionária durante os horários de pico comercial, diminuindo a dependência de termelétricas poluentes e reduzindo a pegada de carbono do estabelecimento.

Eficiência Energética via Algoritmo: A distribuição inteligente de energia evita o desperdício térmico em transformadores e otimiza o uso de eletricidade disponível, permitindo a instalação de eletropostos rápidos mesmo em locais com infraestrutura de rede severamente limitada.

Sustentabilidade de Negócio: A mitigação de multas contratuais por excesso de demanda torna o modelo financeiramente viável e altamente escalável para frotas comerciais em expansão.

🤖 Inteligência Artificial: Chatbot ChargeOps (Chain of Thoughts)
O Assistente Técnico ChargeOps foi desenvolvido para atuar como primeira linha de suporte no eletroposto comercial. Em vez de simplesmente gerar respostas genéricas baseadas em palavras-chave, ele utiliza o princípio de Chain of Thoughts (Cadeia de Pensamento):

Ele recebe a pergunta ou reclamação do usuário (Ex: "Por que meu carro está carregando lento?").

Internamente, a árvore de decisão da IA analisa os dados reais e atuais da telemetria do Inversor GoodWe.

A IA pondera se o sistema está em estado de "Contrapartida Ativa" por sobrecarga predial.

Com base no diagnóstico técnico do ecossistema, ela constrói uma justificativa empática e humanizada, explicando o motivo técnico de segurança energética de forma clara para o motorista, otimizando o custo operacional de suporte técnico.

💻 Instruções de Uso e Execução da Simulação
O protótipo digital foi construído em Python e está totalmente pronto para execução em ambiente de nuvem do Google Colab.

Pré-requisitos:
Apenas um navegador de internet com conta Google ativa.

Nenhuma instalação local é necessária (o código utiliza bibliotecas nativas como time, random e pandas).

Passos para Execução:
Abra o arquivo do notebook (.ipynb) disponibilizado neste repositório ou copie o script do bloco principal.

Acesse o Google Colab.

Crie uma nova Célula de Código (+ Código), cole o script e clique no botão de Play (Executar).

O sistema iniciará a simulação dinâmica simulando a telemetria IoT. O algoritmo irá ler sensores em loops de 2 segundos, gerando cenários com variações climáticas repentinas e mudanças aleatórias de fluxo de carros.

Após os ciclos, um relatório tabular estruturado em DataFrame (representando a Plataforma SEMS) será renderizado na tela, seguido pela resposta em tempo real formulada pela árvore de pensamento da IA ChargeOps.

Este projeto faz parte das entregas obrigatórias da Sprint 2 da FIAP em parceria com o GoodWe Challenge 2026.
