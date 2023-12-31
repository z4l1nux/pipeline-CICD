# Pipeline-CICD

No fluxo de desenvolvimento de software ilustrado na imagem, o processo começa com os desenvolvedores realizando 'commit' e 'push' de suas alterações no GitHub. Estas ações disparam o pipeline CI/CD via GitHub Actions, que executa ferramentas de segurança como Horusec para análise estática e SonarQube para identificar problemas de qualidade e segurança no código.
Após a aprovação destas etapas, as imagens de container são armazenadas em um registro de imagens (Docker Hub). Com o ArgoCD, uma ferramenta de entrega contínua para Kubernetes, os manifestos da aplicação são sincronizados e promovidos automaticamente para ambientes de teste (HML) e, com a aprovação necessária, para produção.
O pipeline também inclui ZAP DAST para testes dinâmicos e identificação de vulnerabilidades em tempo real. Finalmente, a aplicação é implantada no ambiente de produção hospedado em um cluster AWS EKS, tornando-a disponível globalmente. Este ciclo destaca a importância da automação e da segurança no desenvolvimento de software moderno.

![Captura de tela 2023-11-10 122732](https://github.com/z4l1nux/pipeline-CICD/assets/124527204/65d42fdc-6004-4b76-afdf-798b53e3697f)

# Diagrama de Fluxo de Gestão de Vulnerabilidades

Neste fluxo os Desenvolvedores fazendo um 'commit' no GitHub, ativando o Workflow automatizado. Este Workflow é a espinha dorsal do nosso processo de integração contínua, verificando automaticamente o código em busca de problemas de segurança e qualidade.
Assim que o Workflow é concluído, os resultados são enviados para o Horusec Manager e SonarQube, uma plataforma robusta que inspeciona a qualidade do código e identifica vulnerabilidades. Porém antes deste processo de envio, no ambiente de testes e HML existem aprovadores automatizados que podem quebrar a Build.
Com os resultados em mãos, entramos na etapa de Gestão de Vulnerabilidades, que é um processo crítico que segue a análise. Aqui, todas as vulnerabilidades detectadas são cuidadosamente classificadas e priorizadas, garantindo que nossa atenção esteja focada nas questões mais críticas que requerem ação imediata.
Após a priorização, o passo seguinte é a correção. Os desenvolvedores são informados sobre as vulnerabilidades e trabalham no fechamento dos problemas. Este é um ciclo iterativo de identificação, classificação, correção e verificação que garante que nosso código permaneça tão seguro quanto possível.
Finalmente, após as correções, os Desenvolvedores Conferem o código novamente, assegurando que todas as mudanças sejam implementadas corretamente e que novas vulnerabilidades não tenham sido introduzidas durante o processo de correção. Este fluxo nos permite manter uma postura de segurança proativa e responsiva dentro do ciclo de desenvolvimento de software.

![Captura de tela 2023-11-10 131319](https://github.com/z4l1nux/pipeline-CICD/assets/124527204/41228755-226e-417d-8950-ab30cbc95b20)
