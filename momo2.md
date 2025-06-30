### **Configuração de Monitoramento e Alertas**
  1.  **Criar Alerta de Exclusão de VM**:
      
      *   Acessar **Monitoramento** > **Alertas** > **Nova regra de alerta**.
          
      *   Selecionar **Grupo de recursos** ou **VM específica** como destino.
          
      *   Condição:
          
          *   Escolher **Registro de atividades** > **Exclusão de recurso**.
              
          *   Filtro: Tipo de recurso = **Microsoft.Compute/virtualMachines**.
              
      *   Ação:
          
          *   Criar **Grupo de Ações** (email, SMS, webhook).
              
          *   Anotar email cadastrado para validação.
              
      *   Detalhes: Nomear alerta (ex: "AlertaExclusãoVM") e descrição.
          
      *   Revisão: Confirmar configurações e criar.
          
  2.  **Teste do Alerta**:
      
      *   Excluir VM (via portal ou CLI).
          
      *   Aguardar 5-10 minutos para disparo do alerta.
          
      *   Verificar recepção do email com detalhes do evento (usuário que excluiu, horário, região).
          
  3.  **Observações**:
      
      *   Alerta dispara **após** a exclusão do recurso, não previne a ação.
          
      *   Email pode ir para spam (adicionar remetente à lista segura).
          
      *   Alerta permanece ativo mesmo após VM ser excluída (necessário deletar manualmente).
          
### **Validação e Troubleshooting**

*   **Passos para Validar**:
    
    1.  Deletar VM propositalmente (testar via CLI ou portal).
        
    2.  Verificar email cadastrado no Grupo de Ações.
        
    3.  Acessar **Registro de Atividades** (portal > Monitoramento) para confirmar evento de exclusão.
        
*   **Problemas Comuns**:
    
    *   **Email não recebido**:
        
        *   Verificar spam/junk folder.
            
        *   Confirmar configuração correta do Grupo de Ações.
            
        *   Testar com outro email.
            
    *   **Alerta não dispara**:
        
        *   Garantir que a condição do alerta inclua o tipo de recurso correto.
            
        *   Alertas de registro de atividades podem ter atrasos de até 10 minutos.
            
*   **Dicas Úteis**:
    
    *   Usar **Tags** para organizar alertas por ambiente (dev/prod).
        
    *   Para evitar exclusão acidental, ativar **bloqueio de recurso** (Lock Resource).
        
    *   Alertas podem ser integrados a **Azure Logic Apps** para automações (ex: criar nova VM após exclusão).
        

**Nota de Estudo**:

*   Alertas de exclusão são críticos para auditoria e segurança.
    
*   Grupos de Ações reutilizáveis simplificam gestão de notificações múltiplas.
    
*   Alertas não substituem backups regulares (usar **Azure Backup** para proteção completa).
