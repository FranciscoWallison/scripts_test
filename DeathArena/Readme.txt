                    ___________________                      
                   /   _____/\______   \                     
                   \_____  \  |    |  _/                     
                   /        \ |    |   \                     
                  /_______  / |______  /                     
                          \/         \/                      
                   [ Advanced Scripts ]                      
                                                        v1.2 
	----------------------------------------------------------
	-            Documenta��o Oficial do Sistema             -
	----------------------------------------------------------
	Autor: Romulo de Sousa Mangueira. (SoulBlaker)
	Reposit�rio: https://github.com/SoulBlaker
	Reposit�rio do Sistema: https://github.com/SoulBlaker/scripts_test/tree/master/DeathArena
	Contato: romulo_c4aos@hotmail.com (N�o � para suporte)
	
	* �ndice
		1.0 - Fun��es do Script NPC
			1.1 - Instala��o do Script NPC
			1.2 - Configura��es do Script NPC
			1.3 - Instala��o do Banco de Dados
			1.4 - Instala��o do Unreal Tournament PATCH
		2.0 - Ranking Web.
			1.1 - Instala��o dos arquivos na web.
			1.2 - Configura��es dos arquivos web.
			1.3 - Instala��o do Banco de Dados.
		3.0 - Utilizando o sistema in-game
			1.1 - Acesso menu de administrador.
			1.2 - Gerenciando Grupos de restri��es.
			1.3 - Gerenciando Regras ao Grupo de Restri��es.
			1.4 - Gerenciando Arenas.
			1.6 - Gerenciando Rankings.
	----------------------------------------------------------
	
	1.0 - Fun��es do Script NPC
		
			Este npc tem a fun��o de prover arenas de batalhas entre jogadores com personaliza��es administrativa.
			O administrador do servidor pode cadastrar 120 arenas distinta de um tipo (Arena de Jogadores vs Jogadores, 
		Cl�ns vs Cl�ns ou Grupos vs Grupos).
			Cada tipo suporta no total de 120 arenas (total: 360) arenas que podem
		ser cadastrada.
			Cada arena deve ser vinculada a um Grupo de Restri��o e cada Grupo de restri��o suporta 120 itens e 120 classes
		a ser restringida.
			Cada arena tem pessoalmente suas configura��es de acesso como m�ximo de jogadores, minimo de base ou m�ximo de base,
		podendo ser ilimitada ou desabilitada.
			Este npc possui um Ranking distinto por tipos (Jogadores, Cl�ns ou Grupos) com filtragem por vit�rias, derrotas ou
		proporcional de vit�rias sobre derrotas, pode ser acess�vel via o comando '@daranking'.
			Este npc tamb�m possui um sistema de sons podendo ser desativado, baseado no Unreal Tournament.
			O administrador pode acessar o painel administrativo, se dirigindo at� o npc ou utilizando o comando '@damanager'.
	
	1.1 - Instala��o do Script NPC

		Para instalar o script em seu servidor, copie o arquivo 'npc/death_arena.txt' e cole na pasta 'npc' do seu emulador,
	abra o arquivo 'noc/scripts.conf' e coloque no final do arquivo 'npc: npc/death_arena.txt'.
	
	1.3 - Configura��es do Script NPC
	
		Abra o arquivo 'npc/death_arena.txt' e siga com as seguintes configura��es:
		
			Var: $@da_BasicSettings$
			Type: Array
			Desc: Respons�vel pelas configura��es b�sicas do npc.
			Index:
					0 -> N�vel de GM para acessar o painel de administra��o.
					1 -> Sistemas de eventos de avisos nas arenas.
							0: Desativado
							1: Habilitar mensagens globais no mapa avisando quando o jogador derrota outro.
							2: Habilitar sons do Unreal Trounament.
							3: Habilitar ambos.
					2 -> Habilitar janela de chat que ser� exibido em cima do npc. (Abre suporte a um chat no npc com no m�ximo de 20 jogadores)
					3 -> Mensagem a ser exibida na janela de chat (se a op��o acima estiver habilitada) ou sobre refer�ncia ao npc.
					4 -> Nome do npc a ser exibido nas janelas de dialogo.
					5 -> Checar se um item na restri��o seja carta, se ela est� equipada em um equipamento. (Em planejamento ainda)
					6 -> Total de resultados a ser exibido por p�gina no raking do NPC. (M�ximo 120 resultados)
					7 -> N�vel de GM para utilizar o comando @daranking, 0 � para todos os jogadores.
			