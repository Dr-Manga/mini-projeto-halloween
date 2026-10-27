# Relatório Executivo: Auditoria e Insights Comerciais de Halloween

## 1. Diagnóstico da Base e Limpeza de Dados
A auditoria sobre a base de 1.500 transações de Halloween identificou ruídos textuais e inconsistências cadastrais severas. Por meio de Expressões Regulares (Regex) e normalização de strings, foram padronizadas as categorias em fantasia (979), acessório (503) e sem categoria (18), além de consolidar os canais de venda em Web (666), Loja física (551) e Mercado (283).

## 2. Refutação da Hipótese da Gestão
A diretoria sustentava a premissa de que qualquer pedido sem data de entrega registrada correspondia necessariamente a um cancelamento. A análise quantitativa refutou categoricamente essa hipótese:
- Dos 139 pedidos sem data de entrega na base higienizada, 108 foram de fato cancelados, porém 31 pedidos constavam com status Concluído (exemplos: pedidos 1170, 990, 740, 45 e 720).
- Conclusão: Trata-se de um gargalo de preenchimento operacional e falha de integração no sistema logístico, e não de perda de clientes por desistência.

## 3. Inconsistências Numéricas e Integridade Analítica
Foram mapeadas 19 transações com corrupção de valores numéricos (1,27% da base), sendo 7 pedidos com quantidades nulas ou negativas (ex: pedido 630 com quantidade -1) e 12 registros com preço unitário ausente (NaN). Para preservar a confiabilidade métrica e viabilizar modelos de Machine Learning futuros, esses registros foram isolados, consolidando um dataset analítico de 1.481 linhas válidas.

## 4. Sazonalidade e Dinâmica de Vendas
O tratamento de datas revelou 4 registros corrompidos e confirmou a forte sazonalidade do evento:
- Outubro de 2024 registrou 388 vendas, ante 75 em agosto e 104 em setembro.
- Outubro de 2025 atingiu o pico de 405 vendas, superando com folga agosto (62) e setembro (92).
- Mais de 53% das conversões anuais concentram-se estritamente na janela de outubro, com arrefecimento imediato em novembro.

## 5. Recomendações Estratégicas
1. **Auditoria de TI e Logística:** Implementar travas de validação no checkout para bloquear quantidades <= 0 e obrigatoriedade de baixa de entrega pelos entregadores.
2. **Planejamento de Estoque:** Antecipar compras e reforço de capacidade operacional já no fim de setembro para maximizar a captura do pico de outubro.
