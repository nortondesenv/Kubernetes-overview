# Kubernetes-overview

> Kubernetes é uma plataforma de código aberto para gerenciar serviços e cargas de trabalho em contêineres. Alguns de seus recursos incluem:
> 
- **Descoberta de serviço e balanceamento de carga:** Ele pode expor um contêiner usando o nome DNS ou seu próprio endereço IP e, se o tráfego para um contêiner for alto, o Kubernetes pode balancear a carga e distribuir o tráfego de rede.

- **Orquestração de armazenamento:** Ele permite que você montar automaticamente um sistema de armazenamento de sua escolha, como o armazenamento local, os provedores de nuvem pública, e muito mais.

- **Implementações e reversões automatizadas :** automatize o Kubernetes para criar novos contêineres para sua implantação, remova os contêineres existentes e adote todos os seus recursos para o novo contêiner

- **Autocorreção:** Reinicia os contêineres que falham, substitui os contêineres, elimina os contêineres que não respondem à verificação de integridade definida pelo usuário

- **Gerenciamento de segredo e configuração:** Permite armazenar e gerenciar informações confidenciais, como senhas, tokens OAuth e chaves SSH

**Componentes do Kubernetes**

**Pod:**

- A menor unidade do Kubernetes (K8s)
- É uma abstração sobre o contêiner
- Todos os contêineres no mesmo pod compartilharão os mesmos recursos e rede local.
- Os contêineres podem se comunicar facilmente com outros contêineres no mesmo pod.
- Cada pod recebe seu próprio endereço IP e, quando um pod morre, um novo IP é atribuído.
- Os pods são a unidade de replicação no K8s. Se seu aplicativo se tornar popular e uma única instância de pod não puder carregar a carga, o Kubernetes pode ser configurado para implantar novas réplicas de seu pod no cluster.

**Serviço:**

- O Kubernetes fornece aos pods seus próprios endereços IP e um único nome DNS para um conjunto de pods e pode fazer o balanceamento de carga entre eles.
- Um cliente envia uma solicitação ao endereço IP estável e a solicitação é roteada para um dos pods no serviço.
- O ciclo de vida de um pod e serviço não está conectado. Portanto, se um pod morre, seu serviço não é afetado.
- Este próprio componente é um balanceador de carga.
- Um serviço identifica seus pods membros com um seletor. Para que um pod seja membro do serviço, ele deve ter todos os rótulos especificados no seletor.

**Volume:**

Os arquivos em disco em um contêiner são efêmeros ( *duram pouco tempo* ), o que apresenta alguns problemas para aplicativos não triviais quando executados em contêineres.

Problemas:

1. Perda de arquivos quando um contêiner trava. O kubelet reinicia o contêiner, mas com uma lousa em branco.
2. Compartilhamento de arquivos entre contêineres executados juntos em a `Pod`
    
    

**ConfigMap:**

- Os ConfigMaps permitem que você separe suas configurações de seus pods e componentes.
- Isso torna as configurações do pod mais fáceis de alterar e gerenciar e evita a codificação dos dados de configuração de acordo com as especificações do pod.
- Vamos definir os dados de configuração separadamente do código do aplicativo.
- Armazene dados não confidenciais em pares de valores-chave.
- Os pods leem os dados deste mapa de configuração.
