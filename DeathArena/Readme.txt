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
			1.4 - Instala��o do Unreal Tournament e arquivos do PATCH
		2.0 - Ranking Web
			2.1 - Instala��o do Ranking Compacto
			2.2 - Instala��o do Ranking de Visualiza��o Completa
			2.3 - Configura��es do Ranking Web
		3.0 - Utilizando o sistema in-game
			1.1 - Acesso menu de administrador
			1.2 - Gerenciando Grupos de restri��es
			1.3 - Gerenciando Regras ao Grupo de Restri��es
			1.4 - Gerenciando Arenas
			1.6 - Gerenciando Rankings
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
	
	1.2 - Configura��es do Script NPC
	
		Abra o arquivo 'npc/death_arena.txt' e siga com as seguintes configura��es:
		
			Var: $@da_BasicSettings$
			Tipo: Array
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
			
			Var: $@da_DataBase$
			Tipo: Array
			Desc: Respons�vel pelas configura��es do banco de dados.
			Index:
					0 -> Banco de Dados de arenas.
					1 -> Banco de Dados dos grupos de restri��es.
					2 -> Banco de Dados das regras de restri��es.
					3 -> Banco de Dados do Ranking.
					
			Var: $@da_SoundEffect$
			Tipo: Array
			Desc: Respons�vel pelas configura��es de sons do Unreal Tournament.
			Usagem: <mortes>, "<wav>"
			Index:
					mortes: A quantidade de mortes para o som ser tocado, se o �ndice da matriz for 0, ele ser� repetido quando o ultrapassar a
				            quantidade m�ximo de mortes.
					wav: Arquivo na sua pasta data.
			Exemplo:
					10, "som_01.wav"	-> Ele ir� executar o som quando o jogador matar 10 jogadores.
					20, "som_02.wav"	-> Ele ir� executar o som quando o jogador matar 20 jogadores.
					
	1.3 - Instala��o do Banco de Dados

		Esse sistema utiliza o sistema sql como banco de dados, para isso voc� requer ter um servidor recomendado o 'mySQL 5.6.14'.
		A instala��o pode ser feita via Terminal ou utilizando o phpMyAdmin. Os arquivos do banco de dados se encontra em 'sql-files/death_arena.sql'.
		
		Para instalar via terminal unix, basta executar este comando:
		
		mysql -u <usuario> -p <banco_de_dados> < <diretorio>death_arena.sql
		
			usuario: Usu�rio do banco de dados.
			banco_de_dados: Banco de dados aonde ser� importada a tabela.
			diretorio: Diret�rio at� a tabela.
			
		Exemplo:
				1 -> mysql -u ragnarok -p ragnarok < sql-files/death_arena.sql
				2 -> mysql -u ragnarok -p ragnarok < home/Server/death_arena/sql-files/death_arena.sql
				
		Para instalar via phpMyAdmin (v4.0.9), basta acessar em seu navegador o endere�o 'http://127.0.0.1/phpmyadmin', selecionar o banco de dados aonde
		deseja adicionar o banco de dados, ir na aba 'Importar', clicar no upload button 'Escolher Arquivo' selecionando o mesmo e clicar no bot�o Executar.
		
	1.4 - Instala��o do Unreal Tournament e arquivos do PATCH
	
		Para instalar os sons do Unreal Tournament e os arquivos do patch, pasta a pasta 'wav' e 'texture' que se encontra no diret�rio 'patch/data' e adicionar na sua pasta data ou
		copiar o arquivo 'deatharena.grf' que se encontra no diret�rio 'patch', colar no diret�rio do seu jogo e adicionar ao arquivo DATA.INI.
		
		Exemplo DATA.ini:
			1=seuro.grf
			2=deatharena.grf
			3=data.grf
		
	
	2.0 - Ranking Web
	
		Este sistema possue dois tipos de Ranking, um de visualiza��o compacta que pode ser posto em um lugar especifico do seu web site ou um de visualiza��o
	completa, que pode ser vinculado ao seu web site.
		Este sistema requer um servidor PHP instalado em sua hospedagem, recomendado o Apache (v2.4.7)
		
	2.1 - Instala��o do Ranking Compacto
		Crie um diret�rio em sua hospedagem, copie os arquivos da pasta 'www' ao diret�rio criado.
		Adicione o c�digo abaixo em um lugar especifico do seu web site:
		
		<iframe frameborder="0" src="../compact.php" width="222" height="500" scrolling="no"></iframe>
		
	2.2 - Instala��o do Ranking de Visualiza��o Completa
	
		Crie um diret�rio em sua hospedagem, copie os arquivos da pasta 'www' ao diret�rio criado.
		Acesse o ranking com o domino da sua hospedagem / diret�rio que voc� criou, exemplo: http://127.0.0.1/deatharena
		
	2.3 - Configura��es do Ranking Web
	
		Abra o arquivo 'scripts/source.php' em um editor de texto, e segue com as seguintes configura��es:
		
		Var: $mysqlDB
		Tipo: Array
		Desc: Respons�vel pelas configura��es de usu�rios, senhas e tabelas do banco de dados.
		Index:
				base: Banco de Dados aonde se encontra as tabelas.
				user: Usu�rio de acesso ao banco de dados.
				pass: Senha do usu�rio de acesso ao banco de dados.
				host: Local aonde se encontra o servidor de banco de dados.
				ranking: Tabela de Ranking no banco de dados.
				guild_db: Tabela de Cl�ns no banco de dados.
				party_db: Tabela de Grupos no banco de dados.
				char_db: Tabela de personagens no banco de dados.
				
		Var: $max_row
		Tipo: Integer
		Desc: Quantidade de resultados a ser exibido por p�gina.