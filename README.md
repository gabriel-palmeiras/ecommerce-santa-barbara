Título: Transformação Digital e E-commerce Omnichannel: Casa de Velas Santa Bárbara
Papel: Desenvolvedor Full-Stack / Arquiteto de Soluções

1. O Desafio e Contexto de Negócio
Este projeto nasceu para resolver uma dor operacional crítica de um parceiro de negócios: uma loja física de velas artesanais premium com alto volume de vendas em grandes marketplaces (Mercado Livre, Shopee e TikTok Shop), mas com a gestão interna de estoque e pedidos ainda feita no papel. O desafio foi digitalizar toda a operação criando duas frentes: uma vitrine B2C premium focada no modelo "Compre e Retire", e um sistema de gestão centralizado (Back-office). O sistema unifica o controle da loja física com o digital e realiza a integração via API com o TikTok Shop, criando um ecossistema operacional 100% dinâmico e omnichannel.

2. Decisões Arquiteturais e Frontend de Alta Performance
Para garantir que a experiência do cliente final fosse ultrarrápida (essencial para conversão e SEO) e o painel administrativo robusto, a arquitetura foi dividida estrategicamente:

Renderização no Servidor (Next.js App Router): Toda a carga pesada de consultas ao catálogo e histórico de compras ocorre no servidor (Server Components). Isso elimina carregamentos lentos na tela do usuário e protege as consultas ao banco contra engenharia reversa.

Carregamento Imediato: O uso de interceptadores de erro e otimização da hidratação de componentes garante que o usuário nunca enfrente "telas brancas" ou lentidão ao navegar pelas categorias.

Design Minimalista e Focado no Produto: Estilização desenvolvida com Tailwind CSS, garantindo uma interface mobile-first elegante que reflete o posicionamento premium da marca.

3. Engenharia de Segurança e Separação de Acessos
Lidando com dados de clientes e controle de estoque, a proteção contra acessos indevidos (como um cliente tentando ver o pedido de outro) foi tratada na raiz do sistema:

Segurança no Banco de Dados (PostgreSQL RLS): Assim como em sistemas de alta complexidade, a segurança foi injetada diretamente no banco de dados via Supabase. Políticas de nível de linha garantem que o cliente só tenha acesso aos seus próprios recibos e reservas.

Isolamento Administrativo: Para o painel de gestão, o sistema utiliza uma camada de privilégios elevados apenas no ambiente de servidor. Isso cria uma separação total entre o que o cliente B2C pode acessar e o que o gestor da loja física pode controlar, inviabilizando falhas de permissão.

4. Motor de Regras de Negócio e Lógica Integrada (Destaque do Projeto)
O sistema foi desenhado para ser guiado por dados, impedindo gargalos operacionais entre o clique do cliente e a separação do produto na loja física:

Máquina de Estados de Pedidos: O fluxo de vendas segue etapas rigorosas controladas pelo backend (Aguardando Confirmação -> Pago -> Retirado). O sistema bloqueia qualquer alteração de status fora desse fluxo lógico, prevenindo erros na entrega.

Motor Dinâmico de Fidelidade (Cashback): O cálculo de cashback e vouchers é feito em tempo real, agregando o histórico do cliente de forma dinâmica, sem precisar gravar cálculos parciais no banco de dados.

Integração API (TikTok Shop): Sincronização direta que automatiza a entrada de pedidos da rede social para o fluxo de gestão interno da loja, centralizando o estoque em uma única fonte de verdade.
