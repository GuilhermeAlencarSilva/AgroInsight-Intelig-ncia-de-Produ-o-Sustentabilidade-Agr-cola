🌾 AgroInsight - Inteligência de Produção & Sustentabilidade Agrícola

Projeto analítico sênior desenvolvido para demonstrar competências em modelagem de dados, análise de negócios, Power BI e storytelling executivo, aplicado ao contexto do agronegócio.

📌 Visão Geral

Empresas do agronegócio enfrentam desafios crescentes relacionados a:

Produtividade agrícola

Custos operacionais

Impactos climáticos

Sustentabilidade ambiental (ESG)

O AgroInsight foi criado para apoiar a tomada de decisão estratégica, integrando dados de produção, clima, custos e indicadores ambientais em um dashboard analítico e executivo.

🎯 Objetivos do Projeto

Avaliar produtividade por hectare

Monitorar custos de produção

Comparar safras e regiões

Analisar impactos climáticos

Medir sustentabilidade da operação

Criar um case sólido de portfólio profissional

🧠 Nível do Projeto

Sênior / Avançado

Foco em:

Modelagem estrela

Métricas bem definidas

Boas práticas de Power BI

Storytelling executivo

Análise crítica de dados

🧱 Modelo de Dados

O projeto utiliza modelo estrela, com uma tabela fato central e dimensões desnormalizadas.

⭐ Tabela Fato

Fato_Producao_Agricola

📐 Dimensões

Dim_Tempo

Dim_Cultura

Dim_Fazenda

Dim_Regiao

Dim_Clima

Dim_Insumo

📌 Relacionamentos:

1:* (Dimensão → Fato)

Filtro unidirecional

Dim_Tempo conectada via ID_Tempo

📊 KPIs e Métricas

Principais métricas desenvolvidas em DAX:

Área Total Plantada

Produção Total (ton)

Produtividade Média (ton/ha)

Custo Total

Receita Total

Margem (%)

Custo por Hectare

Emissão CO₂ Total

Consumo Total de Água

Produtividade YoY / Safra

Eficiência Ambiental

📌 Todas as métricas respeitam o contexto do modelo estrela e evitam agregações artificiais.

📐 MEDIDAS DAX — PROJETO AGROINSIGHT

📌 CONVENÇÕES

Todas as medidas usam a tabela Fato_Producao_Agricola

Modelo estrela respeitado

Nenhuma coluna calculada

Apenas medidas

🌱 PRODUÇÃO E ÁREA
🔹 Área Total Plantada
Área Total Plantada =
SUM ( Fato_Producao_Agricola[Area_Hectares] )

🔹 Produção Total (ton)
Produção Total (ton) =
SUM ( Fato_Producao_Agricola[Producao_Toneladas] )

🔹 Produtividade Média (ton/ha)
Produtividade Média (ton/ha) =
DIVIDE (
    [Produção Total (ton)],
    [Área Total Plantada]
)

💰 CUSTOS, RECEITA E RENTABILIDADE
🔹 Custo Total
Custo Total =
SUM ( Fato_Producao_Agricola[Custo_Total_R$] )

🔹 Receita Total
Receita Total =
SUM ( Fato_Producao_Agricola[Receita_Estimada_R$] )

🔹 Margem (%)
Margem (%) =
DIVIDE (
    [Receita Total] - [Custo Total],
    [Receita Total]
)

🔹 Custo por Hectare
Custo por Hectare =
DIVIDE (
    [Custo Total],
    [Área Total Plantada]
)

🌍 SUSTENTABILIDADE E ESG
🔹 Emissão CO2 Total
Emissão CO2 Total =
SUM ( Fato_Producao_Agricola[Emissao_CO2] )

🔹 Consumo Total de Água
Consumo Total de Água =
SUM ( Fato_Producao_Agricola[Consumo_Agua_m3] )

🔹 Eficiência Ambiental

Métrica usada no Ranking de Fazendas mais eficientes

Eficiência Ambiental =
DIVIDE (
    [Produção Total (ton)],
    DIVIDE ( [Consumo Total de Água], 1000 )
        + [Emissão CO2 Total]
)


📌 Água normalizada para evitar distorção de escala.

🌦️ CLIMA
🔹 Precipitação Média (mm)

Usada no gráfico Produção x Precipitação

Precipitacao Média (mm) =
AVERAGEX (
    Fato_Producao_Agricola,
    RELATED ( Dim_Clima[Precipitacao_mm] )
)


📌 Itera sobre a FATO para garantir contexto temporal.

📆 ANÁLISE TEMPORAL
🔹 Produção Safra Anterior
Produção Safra Anterior =
CALCULATE (
    [Produção Total (ton)],
    SAMEPERIODLASTYEAR ( Dim_Tempo[Data] )
)

🔹 Produtividade YoY / Safra
Produtividade YoY / Safra =
DIVIDE (
    [Produção Total (ton)] - [Produção Safra Anterior],
    [Produção Safra Anterior]
)

📊 MEDIDAS AUXILIARES (USO EM VISUAIS)
🔹 Ranking Fazendas (Eficiência)
Ranking Eficiência =
RANKX (
    ALL ( Dim_Fazenda[Fazenda] ),
    [Eficiência Ambiental],
    ,
    DESC
)


📌 Usada para Top N e ordenação.


📈 Dashboard Power BI

O dashboard é composto por 4 páginas analíticas, cada uma com objetivo claro.

📄 Página 1 — Visão Geral da Safra

<img width="807" height="802" alt="pag1" src="https://github.com/user-attachments/assets/cbe42a21-9d45-4bfd-9af9-515c1234927b" />

Visão executiva do desempenho agrícola:

Produção

Receita

Margem

Evolução temporal

Comparação por cultura e região

📄 Página 2 — Produtividade & Custos

<img width="614" height="799" alt="pag2" src="https://github.com/user-attachments/assets/debaa35c-c74a-4e10-9817-4f11e8428110" />

Análise operacional:

Eficiência por fazenda

Custos por cultura

Relação área × produção

Comparações regionais

📄 Página 3 — Clima & Impacto

<img width="616" height="801" alt="pag3" src="https://github.com/user-attachments/assets/5b061ca5-c9f1-46af-978c-8bbc26b7d687" />

Impacto climático na produção:

Produção × Precipitação

Análise por safra

Tipos de clima

Heatmap regional

📄 Página 4 — Sustentabilidade

<img width="802" height="803" alt="pag4" src="https://github.com/user-attachments/assets/83a7950b-9a26-4c9e-8233-1a2c47ecb340" />

Análise ESG:

Emissão de CO₂

Consumo de água

Ranking de fazendas mais eficientes

Indicadores ambientais consolidados

🎨 Identidade Visual

O layout segue padrão corporativo e ESG, com paleta baseada na identidade do projeto:

Verde (produtividade / sustentabilidade)

Azul (clima / água)

Laranja (custos / emissões)

Tons neutros para leitura executiva

A identidade visual foi pensada para consistência entre marca e dashboard.

🧪 Geração dos Dados

Base simulada, porém realista

250.000 registros

Período: 2023–2024

Alta dispersão

Distribuições não homogêneas

Relações causais (clima, região, cultura)

📌 O objetivo não é volume artificial, mas qualidade analítica.

🧩 Principais Decisões Analíticas

Médias não forçadas para gerar contraste artificial

Diferenças pequenas são preservadas (realismo)

Eficiência ≠ produtividade

Métricas ambientais normalizadas para evitar distorções

Uso consciente de medidas DAX vs colunas

👤 Autor

Projeto desenvolvido por Guilherme Alencar
Especialista em Análise de Dados, Negócios e Visualização Executiva

📫 LinkedIn: https://www.linkedin.com/in/guilherme-alencar-327413213/
📊 Portfólio: https://github.com/GuilhermeAlencarSilva
