# Teste de carga usando k6

## Introdução
A atividade descrita aqui foi baseada no artigo "Load testing using k6 (load e stress testing com Go)". Esse artigo apresenta o k6, uma ferramenta open-source voltada para realizar testes de carga e stress em aplicações web. Seu principal objetivo é verificar a capacidade de uma aplicação lidar com volumes crescentes de tráfego, garantindo a sua estabilidade e desempenho.

A ferramenta permite a criação de scripts de teste em JavaScript, o que a torna acessível e flexível para diversos tipos de projetos. Além disso, k6 suporta o conceito de Test-Driven Development (TDD), uma prática essencial que permite escrever testes automatizados antes da implementação de funcionalidades. Nesse contexto, o TDD ajuda a garantir que o código desenvolvido atenda aos requisitos de carga desde o início.

## Testes

#### Teste de Fumaça (Smoke Test)

O teste de fumaça é um tipo de teste preliminar que visa garantir que as funcionalidades principais de uma aplicação estejam funcionando corretamente. Ele serve como uma verificação inicial e rápida, para identificar se o sistema está pronto para testes mais detalhados. Se o teste de fumaça falhar, outros testes mais rigorosos podem ser adiados até que o problema seja resolvido.

**Objetivo:** Verificar rapidamente se a aplicação responde como esperado, sem se aprofundar em testes detalhados de performance ou funcionalidade.

Comando ```k6 run tests/smoke-test.js```

![alt text](<imgs/Captura de tela 2024-10-07 210703.png>)

![alt text](<imgs/Captura de tela 2024-10-07 210738.png>)

#### Teste de Carga (Load Test)
O teste de carga é utilizado para verificar como a aplicação se comporta sob uma quantidade crescente de tráfego, até que se atinja um número de usuários que simule o comportamento real de produção. O objetivo é identificar gargalos de desempenho, uso de recursos, e comportamento da aplicação sob carga normal ou elevada.

**Objetivo:** Avaliar o desempenho da aplicação com um número crescente de usuários e identificar como o sistema se comporta sob carga contínua.

Comando ```k6 run tests/load-test.js```

![alt text](<imgs/Captura de tela 2024-10-07 211121.png>)


#### Teste de Picos (Spike Test)
O teste de picos tem como objetivo avaliar a habilidade da aplicação de lidar com aumentos repentinos de tráfego, simulando cenários como promoções ou eventos que atraem uma grande quantidade de usuários em um curto período de tempo.

**Objetivo:** Testar a resiliência da aplicação diante de picos súbitos e temporários de carga.

Comando ```k6 run tests/spike-test.js```

![alt text](<Captura de tela 2024-10-07 211716.png>)


#### Teste de Soak (Soak Test)
O teste de soak, também conhecido como teste de resistência, é executado para verificar o comportamento do sistema sob carga prolongada, geralmente por várias horas ou dias. A ideia é identificar problemas como vazamento de memória ou degradação do desempenho ao longo do tempo.

**Objetivo:** Garantir que a aplicação possa manter o desempenho aceitável por longos períodos de tempo, sem apresentar problemas como queda de desempenho ou consumo excessivo de recursos.

Comando ```k6 run .\breakpoint-test.js```

![alt text](<imgs/Captura de tela 2024-10-07 212413.png>)

Obs: tests interrompido pois a duração era de 24h

### Conceitos de TDD (Test-Driven Development)
O Desenvolvimento Orientado por Testes (TDD - Test-Driven Development) é uma prática de desenvolvimento de software onde os testes são escritos antes da implementação do código. O principal objetivo do TDD é melhorar a qualidade e a confiabilidade do código, garantindo que as funcionalidades implementadas estejam corretas e funcionando conforme esperado. Vamos explorar os principais conceitos do TDD:

**1. Ciclo do TDD**
O TDD segue um ciclo básico de três etapas, conhecido como o ciclo "Red-Green-Refactor" (Vermelho-Verde-Refatorar), que é repetido continuamente durante o desenvolvimento:

**Red (Vermelho):** Escreva um teste que defina a funcionalidade desejada ou o comportamento esperado do sistema. Este teste, inicialmente, falhará (ficará "vermelho"), pois o código necessário ainda não foi implementado.

**Green (Verde):** Escreva o código mínimo necessário para fazer o teste passar (ficar "verde"). Nesta fase, o foco é simplesmente fazer o teste passar, sem se preocupar com a qualidade ou a otimização do código.

**Refactor (Refatorar):** Com o teste passando, o desenvolvedor agora pode melhorar e otimizar o código, garantindo que ele ainda passe nos testes. Essa etapa envolve refatorar o código para torná-lo mais limpo, eficiente ou sustentável, sem alterar o comportamento que já foi testado.

## Conclusão
Através da execução dos exemplos de carga e stress testing com k6, foi possível explorar os benefícios dessa ferramenta no processo de desenvolvimento guiado por testes (TDD). A escrita de scripts de teste antes da implementação permite ao desenvolvedor garantir que a aplicação atenda às expectativas de desempenho desde o início, evitando problemas futuros de performance.

O uso de k6 não apenas facilita a criação de testes automatizados de carga, mas também promove uma cultura de desenvolvimento focada em qualidade e robustez, elementos essenciais em sistemas modernos com alta demanda de tráfego.