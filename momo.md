**Anotações: Criação, Adição e Remoção de Disco em VM no Azure**

### **Criação de VM**

*   Portal Azure:
    
    1.  **Criar VM**:
        
        *   Nome da VM, região (South America/Brazil), imagem (Windows 2025 Datacenter: Azure Edition x64), tamanho (B1s).
        *   Duas zonas, de acordo com disponibilidade com tamanho de VM
        *   Credenciais: Usuário e senha.
        *   Rede: Sem portas abertas, rede marcada para exclusão junto da VM
        *   Disco: Usar disco gerenciado.
        *   Revisão e criação.
        *   Observação: Disco do SO é criado automaticamente (50-127 GB, dependendo da imagem).
            
### **Adição de Disco Extra**

*   Portal Azure:
    
    1.  **Criar e anexar disco**:
        
        *   Acessar VM > **Disks** > **Attach new disk**.
        *   Especificar tamanho (ex: 100 GB), e tipo (HDD/SSD).
        *   Disco aparecerá como **não inicializado** no sistema operacional.
        *   Disco pode ser anexado sem parar a VM (para Windows/Linux modernos).
            
### **Remoção de Disco Extra**

*   Portal Azure:
    
    1.  **Desanexar na Azure**:
        
        *   Acessar VM > **Disks** > Selecionar disco extra > **Detach**.
        *   Disco permanece no grupo de recursos (não é excluído automaticamente).
            
    2.  **Excluir disco (opcional)**:
        
        *   Acessar disco no grupo de recursos > Excluir.
            
    3.  **Observações**:
        
        *   Dados são perdidos se o disco for excluído.
        *   Disco desanexado pode ser reutilizado em outra VM.
        

**Notas de Estudo**:

*   Discos gerenciados (recomendados) simplificam operações (não precisam de contas de armazenamento).
*   Discos podem ser migrados entre VMs (desanexar de uma, anexar a outra).
*   Para backups, usar Azure Backup ou snapshots (não abordado aqui).
