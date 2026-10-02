# Calculadora de Operações - Mercado Futuro - B3

Aplicação web de arquivo único para apoiar a simulação de operações com contratos futuros selecionados da B3. A interface permite combinar parâmetros de mercado e da operação para estimar custos, exposição financeira, margem de garantia, resultado bruto, tributação estimada e resultado líquido.

> **Aviso:** esta ferramenta tem finalidade informativa e de apoio a simulações. Os valores de margem, custos, cotações e tributos podem variar e devem ser conferidos em fontes oficiais, na corretora e, quando aplicável, com profissional habilitado.

## Funcionalidades

- Seleção entre **Mini Índice (WINFUT)**, **Mini Dólar (WDOFUT)** e **Bitcoin B3 (BITFUT)**.
- Exibição das regras de ponto e tick configuradas para cada ativo.
- Cálculo da exposição financeira por contrato e da exposição total da operação.
- Estimativa da margem de garantia total a partir de valor editável por contrato.
- Campos editáveis para taxa de registro e emolumentos BM&F.
- Simulação por **resultado financeiro**, **quantidade de contratos** ou **alvo em pontos/ticks**.
- Conversão automática entre pontos e ticks conforme o ativo selecionado.
- Estimativa de resultado bruto, custos B3, IRRF de Day Trade, DARF complementar e lucro líquido.
- Opção de incluir ou desconsiderar a estimativa de impostos no cálculo.
- Consulta auxiliar de cotações de mercado por APIs públicas, com possibilidade de preenchimento manual.
- Alternância entre tema claro e escuro.
- Interface responsiva baseada em Tailwind CSS.

## Ativos configurados

| Ativo | Identificação na ferramenta | Valor por ponto | Tamanho do tick | Valor do tick |
| --- | --- | ---: | ---: | ---: |
| WINFUT | Mini Índice | R$ 0,20 | 5 pontos | R$ 1,00 |
| WDOFUT | Mini Dólar | R$ 10,00 | 0,5 ponto | R$ 5,00 |
| BITFUT | Bitcoin B3 | R$ 0,10 | 5 pontos | R$ 0,50 |

Os valores padrão de cotação, margem e custos existentes no código funcionam como parâmetros iniciais da simulação e podem ser ajustados na interface.

## Fontes de cotação usadas pela interface

A ferramenta utiliza consultas auxiliares a serviços públicos para preencher cotações aproximadas:

- **WINFUT:** referência do Ibovespa à vista obtida do Yahoo Finance por meio de um proxy público.
- **WDOFUT:** dólar comercial à vista obtido pela AwesomeAPI e convertido para a escala utilizada na interface.
- **BITFUT:** Bitcoin em reais obtido pela AwesomeAPI.

Essas referências são do mercado à vista e podem apresentar atraso ou diferenças em relação ao contrato futuro negociado. Para simulações operacionais, prefira informar manualmente a cotação do contrato exibida em sua plataforma de negociação.

## Tecnologias

- HTML5
- JavaScript (Vanilla JS)
- Tailwind CSS via CDN
- Lucide Icons via CDN
- Google Fonts (Inter)
- AwesomeAPI
- Yahoo Finance, acessado no navegador por meio de AllOrigins

## Como usar

1. Baixe ou clone este repositório.
2. Abra o arquivo `calculadora_operacoes_b3.html` em um navegador moderno com acesso à internet.
3. Selecione o ativo desejado.
4. Revise ou altere cotação, margem e custos.
5. Escolha a variável operacional que deseja avaliar.
6. Informe os parâmetros da operação e acompanhe o resumo calculado automaticamente.

Não há etapa de build, servidor local obrigatório ou instalação de dependências para o funcionamento básico. O acesso à internet é necessário para carregar as bibliotecas externas e utilizar a atualização de cotações.

## Observações sobre os cálculos

A implementação usa regras e parâmetros definidos no próprio arquivo `calculadora_operacoes_b3.html`. Entre outras operações, calcula exposição a partir da cotação e do multiplicador do ativo, agrega custos por contrato e aplica, quando habilitado, uma estimativa tributária total de 20% sobre o resultado positivo após os custos B3, separada na interface em 1% de IRRF e 19% de DARF complementar.

Esses cálculos não substituem a apuração fiscal real, que pode depender de compensação de perdas, operações acumuladas no período, regras vigentes e outros fatores não modelados pela ferramenta.

## Estrutura do projeto

```text
.
├── calculadora_operacoes_b3.html   # interface, estilos e lógica da calculadora
└── README.md    # documentação do projeto
```

## 👤 Autoria e desenvolvimento

Aplicação web desenvolvida de forma independente por **Pablo Phillipe Cândido dos Santos**, destinada à simulação de parâmetros operacionais de contratos futuros selecionados da B3, com estimativas de custos, exposição, margem, quantidade de contratos, alvos em pontos/ticks e resultado financeiro.

O desenvolvimento contou com a utilização de ferramentas de inteligência artificial generativa como recurso auxiliar no processo de desenvolvimento, mantendo-se sob responsabilidade do autor a concepção, implementação, integração e verificação do projeto.

Currículo Lattes: [http://lattes.cnpq.br/9500873674712528](http://lattes.cnpq.br/9500873674712528)

## Limitações

- As cotações automáticas são referências auxiliares e não representam necessariamente o preço do contrato futuro em tempo real.
- Margens de garantia podem variar por corretora, perfil, ativo, horário e condições de mercado.
- Custos e regras tributárias podem mudar e devem ser conferidos antes de qualquer uso prático.
- A ferramenta não executa ordens, não se conecta a conta de corretora e não constitui recomendação de investimento.
