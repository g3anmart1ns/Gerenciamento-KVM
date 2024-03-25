## Opções de linha de comando para gerenciamento do LIBVIRT - KVM

```plaintext
Gerenciamento de Máquinas Virtuais:
-------------------------------------
1. Listar máquinas virtuais:
   virsh list --all

2. Iniciar uma máquina virtual:
   virsh start <nome_da_máquina_virtual>

3. Parar uma máquina virtual:
   virsh shutdown <nome_da_máquina_virtual>

4. Desligar uma máquina virtual de forma forçada:
   virsh destroy <nome_da_máquina_virtual>

5. Verificar o estado de uma máquina virtual:
   virsh domstate <nome_da_máquina_virtual>

6. Pausar uma máquina virtual:
   virsh suspend <nome_da_máquina_virtual>

7. Retomar uma máquina virtual pausada:
   virsh resume <nome_da_máquina_virtual>

8. Reiniciar uma máquina virtual:
   virsh reboot <nome_da_máquina_virtual>

9. Desligar uma máquina virtual de forma segura:
   virsh shutdown <nome_da_máquina_virtual>

10. Criar um instantâneo (snapshot) de uma máquina virtual:
    virsh snapshot-create-as --domain <nome_da_máquina_virtual> <nome_do_instantâneo>

11. Listar instantâneos de uma máquina virtual:
    virsh snapshot-list <nome_da_máquina_virtual>

12. Restaurar uma máquina virtual de um instantâneo:
    virsh snapshot-revert --domain <nome_da_máquina_virtual> <nome_do_instantâneo>

13. Excluir um instantâneo de uma máquina virtual:
    virsh snapshot-delete --domain <nome_da_máquina_virtual> <nome_do_instantâneo>

14. Obter informações detalhadas sobre uma máquina virtual:
    virsh dominfo <nome_da_máquina_virtual>

15. Exibir console de uma máquina virtual:
    virsh console <nome_da_máquina_virtual>


Gerenciamento de Redes Virtuais:
---------------------------------
1. Listar redes virtuais:
   virsh net-list --all

2. Iniciar uma rede virtual:
   virsh net-start <nome_da_rede_virtual>

3. Parar uma rede virtual:
   virsh net-destroy <nome_da_rede_virtual>

4. Excluir uma rede virtual:
   virsh net-undefine <nome_da_rede_virtual>

5. Exibir detalhes de uma rede virtual:
   virsh net-dumpxml <nome_da_rede_virtual>

6. Criar uma nova rede virtual:
   virsh net-define <caminho_para_o_arquivo_xml>

7. Editar as configurações de uma rede virtual:
   virsh net-update <nome_da_rede_virtual> <comando_xml>


Gerenciamento de Pools de Armazenamento:
-----------------------------------------
1. Listar pools de armazenamento:
   virsh pool-list --all

2. Iniciar um pool de armazenamento:
   virsh pool-start <nome_do_pool_de_armazenamento>

3. Parar um pool de armazenamento:
   virsh pool-destroy <nome_do_pool_de_armazenamento>

4. Exibir detalhes de um pool de armazenamento:
   virsh pool-dumpxml <nome_do_pool_de_armazenamento>


Gerenciamento de Discos Virtuais:
----------------------------------
1. Criar uma nova imagem de disco vazio:
   qemu-img create -f qcow2 <caminho_para_o_arquivo_de_imagem> <tamanho>

2. Clonar uma imagem de disco:
   qemu-img create -f qcow2 -b <caminho_da_imagem_original> <caminho_da_nova_imagem>

3. Redimensionar uma imagem de disco:
   qemu-img resize <caminho_para_a_imagem> <novo_tamanho>
```

## V2

```markdown
# Comandos para Gerenciamento do LIBVIRT por Linha de Comando

## Domain Management:
1. **Listar domínios:**
   ```bash
   virsh list --all
   ```

2. **Iniciar um domínio:**
   ```bash
   virsh start <nome_do_domínio>
   ```

3. **Parar um domínio:**
   ```bash
   virsh shutdown <nome_do_domínio>
   ```

4. **Forçar o desligamento de um domínio:**
   ```bash
   virsh destroy <nome_do_domínio>
   ```

5. **Criar um novo domínio:**
   ```bash
   virt-install --name <nome_do_domínio> --memory <quantidade_de_memória> --vcpus <número_de_vcpus> --disk <caminho_do_disco> --os-variant <variante_do_sistema_operacional> --network network=default --graphics none --console pty,target_type=serial
   ```

## Domain Monitoring:
6. **Exibir informações detalhadas sobre um domínio:**
   ```bash
   virsh dominfo <nome_do_domínio>
   ```

7. **Exibir informações de uso de recursos de um domínio:**
   ```bash
   virsh dommemstat <nome_do_domínio>
   ```

## Host and Hypervisor:
8. **Exibir informações do hipervisor:**
   ```bash
   virsh nodeinfo
   ```

9. **Exibir estatísticas do hipervisor:**
   ```bash
   virsh nodememstats
   ```

## Interface:
10. **Listar interfaces de rede:**
    ```bash
    virsh iface-list
    ```

11. **Exibir detalhes de uma interface de rede:**
    ```bash
    virsh iface-dumpxml <nome_da_interface>
    ```

## Network Filter:
12. **Listar filtros de rede:**
    ```bash
    virsh nwfilter-list
    ```

13. **Exibir detalhes de um filtro de rede:**
    ```bash
    virsh nwfilter-dumpxml <nome_do_filtro>
    ```

## Networking:
14. **Listar redes virtuais:**
    ```bash
    virsh net-list --all
    ```

15. **Iniciar uma rede virtual:**
    ```bash
    virsh net-start <nome_da_rede_virtual>
    ```

## Snapshot:
16. **Criar um instantâneo de um domínio:**
    ```bash
    virsh snapshot-create-as --domain <nome_do_domínio> <nome_do_instantâneo>
    ```

17. **Listar instantâneos de um domínio:**
    ```bash
    virsh snapshot-list <nome_do_domínio>
    ```

## Storage Pool:
18. **Listar pools de armazenamento:**
    ```bash
    virsh pool-list --all
    ```

19. **Exibir detalhes de um pool de armazenamento:**
    ```bash
    virsh pool-dumpxml <nome_do_pool_de_armazenamento>
    ```

## Storage Volume:
20. **Listar volumes de armazenamento:**
    ```bash
    virsh vol-list <nome_do_pool_de_armazenamento>
    ```

21. **Exibir detalhes de um volume de armazenamento:**
    ```bash
    virsh vol-dumpxml <nome_do_pool_de_armazenamento> <nome_do_volume>
    ```
