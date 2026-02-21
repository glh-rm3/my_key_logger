# Sobre o projeto
Este projeto está sendo desenvolvido durante meus estudos de sistemas operacionais Linux e programação de baixo e médio nível. A implementação utiliza a biblioteca <linux/input.h>
para interceptar e tratar os eventos brutos provenientes da estrutura input_event. O objetivo principal é aprimorar o entendimento e a lógica de desenvolvimento em um nível mais
próximo ao Kernel.

Na atual implementação, quando o programa é executado, ele escreve todas as teclas digitadas pelo usuário em um arquivo de texto oculto chamado .log.txt. O mapeamento dos
caracteres é gerenciado pelo arquivo customizado keymap.h. Atualmente, as teclas não mapeadas de forma alfanumérica, como as do teclado numérico, teclas de função (F1-F12) 
e caracteres especiais, preenchem o log apenas com um ponto de interrogação, aguardando a futura expansão da lógica de tradução.

# Observações
A captura dos eventos de teclado foi configurada para acessar o descritor de dispositivo /dev/input/event3, uma atribuição que pode variar significativamente dependendo da
sua distribuição Linux e da arquitetura de hardware. O ideal é que, antes de tentar executar o programa, você instale e utilize a ferramenta Evtest com privilégios de superusuário
(sudo) para identificar corretamente qual índice eventX corresponde ao seu dispositivo de teclado atual.

# Problemas enfrentados
A implementação da função caps_status() surgiu para resolver um dos desafios mais complexos do código: a verificação precisa do estado da tecla Caps Lock. Essa rotina foi essencial
para garantir que a escrita no arquivo de texto seja a mais fiel possível à entrada real do usuário, lidando com a necessidade de sincronizar os eventos de estado do teclado com as teclas
efetivamente pressionadas.

