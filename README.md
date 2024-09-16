# ponderada_M7S6

## Introdução

&emsp;&emsp; Com o avanço do uso de sistemas conversacionais em diversos setores, incluindo o financeiro, surgem desafios significativos no que diz respeito à segurança das informações transmitidas e processadas. Em um ambiente regulado como o da indústria financeira no Brasil, que lida com dados sensíveis e regulamentações rigorosas, garantir a integridade, confidencialidade e autenticidade das interações é fundamental. Sistemas conversacionais como chatbots ou assistentes virtuais são frequentemente alvos de ataques cibernéticos que buscam explorar vulnerabilidades para obter informações valiosas. Dentre os principais riscos, destacam-se ataques de injeção de código, vazamento de dados, interceptação de comunicações e engenharia social, que podem comprometer tanto a reputação quanto a conformidade de uma organização com legislações como a Lei Geral de Proteção de Dados (LGPD) [ZIMMER, 2022](#referências).

&emsp;&emsp; Neste contexto, melhorar os requisitos não funcionais de segurança em sistemas conversacionais torna-se um imperativo para assegurar que esses sistemas operem dentro dos parâmetros esperados de proteção de dados e regulamentações financeiras. A implementação de controles completos de segurança deve ser considerada em todas as fases do ciclo de desenvolvimento, abordando desde a autenticação de usuários até a criptografia de comunicações e a prevenção de ataques sofisticados.

## Solução proposta

&emsp;&emsp; Para abordar as vulnerabilidades e reforçar a segurança do sistema conversacional no contexto regulatório financeiro, propomos uma arquitetura modular que integra as melhores práticas de segurança da informação. A arquitetura sugerida está dividida em cinco principais módulos, cada um com responsabilidades específicas que, em conjunto, garantem a proteção do sistema. O diagrama abaixo ilustra a arquitetura proposta:

![Diagrama](diagrama.png)

1. **Interface do usuário**: este módulo gerencia a interação com o usuário, recebendo entradas e exibindo respostas do sistema. Todas as comunicações são criptografadas via HTTPS com TLS 1.3, protegendo contra interceptação de dados. A interface deve prevenir ataques como SQL Injection e Cross-Site Scripting (XSS) e incluir sanitização específica para entradas em linguagem natural, bloqueando comandos maliciosos embutidos. Além disso, deve detectar e mitigar tentativas de manipulação textual ou padrões de linguagem incomuns que possam sinalizar exploração de vulnerabilidades.

2. **Módulo de autenticação**: implementa autenticação multifator (MFA), utilizando biometria, tokens temporários e OAuth 2.0 para integração com terceiros. Nos sistemas conversacionais, a autenticação pode ocorrer por meio de perguntas dinâmicas e reconhecimento de padrões linguísticos, com suporte à biometria de voz para validar identidades em tempo real, complementando a segurança tradicional.

3. **Módulo de criptografia**: garante a criptografia de dados em trânsito e em repouso, utilizando algoritmos como AES-256 e RSA-2048, com rotação periódica de chaves. Além de criptografar dados transacionais, este módulo protege logs de conversas e respostas geradas, evitando vazamentos de informações sensíveis nas interações textuais.

4. **Módulo de análise de comportamento (AI)**: utiliza machine learning para monitorar comportamentos e detectar atividades suspeitas, como padrões anômalos de acesso ou tentativas de fraude. Nos sistemas conversacionais, a AI analisa interações textuais em tempo real, identificando ataques de engenharia social ou manipulações por meio de linguagem. Mudanças de tom, perguntas repetitivas ou tentativas de confundir o sistema acionam alertas automáticos para a equipe de segurança.

5. **Módulo de auditoria e logs seguros**: armazena e criptografa logs detalhados das interações do sistema, garantindo sua imutabilidade e conformidade com a LGPD. Esses logs são auditáveis e monitorados por sistemas de detecção de intrusões (IDS). Nos sistemas conversacionais, tanto os logs de conversação quanto os dados gerados (como respostas automatizadas) são auditados, com políticas de retenção de dados seguras e exclusão conforme necessário.

6. **Banco de Dados Seguro (DB)**: protegido por criptografia e controle de privilégios, o banco de dados armazena informações de usuários, logs de conversas e modelos de linguagem natural. Backups periódicos garantem recuperação segura em caso de ataques. É crucial proteger os modelos de linguagem, que podem conter dados sensíveis e padrões de comportamento, fragmentando e distribuindo dados para evitar exposições em caso de violação.

## Conclusão

&emsp;&emsp; A proposta apresentada busca fortalecer os aspectos de segurança de um sistema conversacional voltado ao setor financeiro, utilizando uma arquitetura modular que permite o gerenciamento eficiente de autenticação, criptografia, monitoramento comportamental e auditoria. Com a implementação dessa solução, o sistema pode garantir a conformidade com as normas da LGPD e outras regulamentações financeiras, além de mitigar os riscos associados a fraudes e vazamentos de dados.

&emsp;&emsp; O esforço necessário para implementar essa solução envolve desde a aquisição de tecnologias específicas, como ferramentas de machine learning para análise de comportamento, até a integração de mecanismos de autenticação e criptografia robustos. Além disso, será necessário realizar treinamentos regulares para o time de desenvolvimento e segurança, garantindo a correta implementação e operação das novas funcionalidades.

## Referências

ZIMMER, Kelvin. Vazamento de dados é prejuízo certo para empresas. Lumiun Blog, 2 mar. 2022. Disponível em: https://www.lumiun.com/blog/vazamento-de-dados-e-prejuizo-certo-para-empresas/. Acesso em: 15 set. 2024.

OWASP. Top 10 Web Application Security Risks – 2021. Disponível em: https://owasp.org/www-project-top-ten/. Acesso em: 15 set. 2024.
