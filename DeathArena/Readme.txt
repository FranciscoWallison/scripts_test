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
	
	1.0 - Fun��es do Script NPC.
		
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