## Principais funções do Núcleo do S.O:

- ### tratamento de interrupções e exceções;
- ### criação e eliminação de processos e threads;
- ### sincronização e comunicação entre processos e threads;
- ### gerencia de memória;
- ### gerencia do sistema de arquivos;
- ### gerencia de dispositivos de entrada e saída;
- ### suporte a redes locais e distribuídas;
- ### segurança e auditoria do sistema;
- ### contabilização de uso do sistema;

# Arquiteturas do Núcleo

- ### O projeto de um sistema operacional é realizado de forma a atender a requisitos operacionais de desempenho, portabilidade, confiabilidade, facilidade de uso, segurança.

- ### O projeto do sistema operacional também depende da arquitetura de hardware e também do tipo de sistema operacional que se deseja construir: batch, tempo compartilhado, tempo real, multi programado, multi processado, etc.

- ### Os primeiros sistemas operacionais eram escritos em Assembly mas isso garantia performance excepcional nos sistemas operacionais mas causava uma dependencia muito grando do sistema operacional em relação ao hardware da máquina e comprometia seriamente a portabilidade. O sistema operacional tinha que ser reescrito se precisasse ser instalado em uma máquina com arquitetura e hardware diferente.

- ### O sistemas operacionais atuais são escritos em linguagens de alto nível, principalmente C e C++ o que garante portabilidade e independencia de hardware conteudo o desempenho é inferior aos antigos sistemas operacionais. Para minimizar este problema, os projetistas ainda usam Assembly para os componentes críticos do sistema operacional tais como drivers e as rotinas de tratamento de exceção que nós vimos na aula passada.

- ### A forma como os componentes do sistema operacional são organizados pode variar, sendo que existem várias arquiteturas de sistemas operacionais disponíveis.

# Arquitetura Monolítica

- ### A arquitetura monolítica foi utilizada nos primeiros sistemas operacionais tais como CP/M, MS- ###DOS e nas primeiras versões do Linux. Nesta arquitetura os componentes do sistema são compilados em módulos separados e depois linkados em um único programa executável. Os módulos são carregados em memória e interagem entre si. A manutenção deste tipo de sistema é bem difícil.

# Arquitetura em Camadas

- ### A arquitetura em camadas surgiu devido a complexidade dos sistema operacionais na medida em que foram evoluindo. Nesta arquitetura o sistema operacional é formado por níveis ou camadas onde as camadas inferior oferecem serviços às camadas superiores. As camadas inferiores são privilegiadas

- ### A vantagem deste tipo de arquitetura é o isolamento das camadas e a segurança e proteção às camadas mais internas onde fica o kernel.

- ### A desvantagem é que o desempenho do sistema é afetado pela troca de modo de acesso. Quando um aplicativo do usuário solicita um serviço da camada kernel é necessário passar por várias outras camadas ( supervisor, executivo ) e realizar várias trocas do modo de acesso.

- ### A maioria dos sistemas operacionais atuais tais como Linux e Windows utilizam o modelo de arquitetura em camadas sendo que estes sistemas implementam apenas duas camadas ( modo usuário e modo kernel ).

# Máquina Virtual

- ### Um sistema operacional é formado por níveis, onde a camada de nível mais baixo é o hardware. Acima dessa camada temos o sistema operacional que oferece serviços para os aplicativos do usuário.

- ### Na arquitetura de máquina virtual existe uma camada intermediária entre o hardware e o sistema operacional chamada gerencia de máquinas virtuais.

- ### Esta camada cria diversas máquinas virtuais independentes, onde cada uma oferece uma cópia virtual do hardware, incluindo os modos de acesso, interrupções, memória, dispositivos de entrada e saída, etc.

- ### Como cada máquina virtual é independente das outras, é possível que cada VM tenha seu próprio sistema operacional e que seus usuários executem suas aplicações como se o computador estivesse dedicado a cada um deles.

- ### Cada máquina virtual é isolada das demais o que proporciona segurança para cada VM. Isto garante também confiabilidade pois uma VM não pode comprometer o estado das outras VMs.

- ### A desvantagem desta arquitetura é a grande complexidade. A camada de gerencia de máquinas virtuais é responsável por compartilhas e gerenciar os recursos do hardware entre as diversas VMS. Esta é uma arquitetura altamente complexa.

# Arquitetura MicroKernel

- ### A arquitetura MicroKernel busca tornar o núcleo do sistema, o kernel o menor e mais simples possível. Nesta arquitetura os serviços do sistema operacional são disponibilizados como serviços. Cada serviço oferece um conjunto de funções como gerência de arquivos, gerência de processos, gerência de memória e etc.

- ### Quando uma aplicação do usuário solicita um serviço é feita uma solicitação ao processo responsável pelo serviço.

- ### A aplicação que solicita o serviço é chamada cliente e o processo que responde à solicitação é chamado de servidor.

- ### O núcleo do sistema se limita a realizar a comunicação entre cliente e servidor. É portanto um núcleo muito mais simples.

- ### Nesta arquitetura, os processos executam suas funções em modo usuário, ou seja, não tem acesso a instruções privilegiadas, não tem acesso aos componentes do sistema. Apenas o núcleo executa em modo kernel. Isto garante que caso haja um erro em um processo o sistema não ficará completamente comprometido. Isso aumenta a disponibilidade do sistema.
