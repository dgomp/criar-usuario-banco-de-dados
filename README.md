# Criando um Novo Usuário no Banco de Dados
  `Como criar usuário no banco de dados, dar permissões e, depois, removê-lo.`

Criado com base no banco de dados AulaDB, da cadeira de Banco de Dados II, do professor [Alex Souza](https://github.com/aasouzaconsult) @aasouzaconsult.

## Logar no Sistema

![](https://lh7-us.googleusercontent.com/Ss4yqcQcHPCU2-ZEXMeH1PLYeKz2f8k119wSlI9hxN2HMj_BCbgpZ6Za172sXN5o--rOX_PYONNiBAow-180Do_6CTz3WWzBCTpwWBy3Y2izZqNdRFtsauHA7icjP8Ayv24ZTrJj8zSN4Mli1XWbtk4)

## Criar Login no Servidor

-   Entrar no Master
	> USE master;

-   Criar login definindo login, senha, banco de dados padrão, tempo de expiração e política.
	> CREATE LOGIN [TesteBDII] WITH PASSWORD=N'123mudar', DEFAULT_DATABASE=[master], CHECK_EXPIRATION=OFF, CHECK_POLICY=OFF;

![](https://lh7-us.googleusercontent.com/wWrTL9xat8-MrDqwKu8SbObfZ3pEmzoCOOGWsNkBXeKk83AKhKtE1OQxoA3vIjWD_bjiISQuodWR40bZn8ovK890csUMXXUxYs0SSlWxux_OTRKAEyIpaFDtvvfidRCCA-CiSf2drGmLVRY94houmkw)

## Criar usuário no banco de dados e associar ao login

-   Conectar-se ao Banco de Dados AulaDB
	> USE AulaDB;

-   Criar usuário
	> CREATE USER [TesteBDII] FOR LOGIN [TesteBDII];

![](https://lh7-us.googleusercontent.com/tOH0-s_Y1Yzna0Z9nfQrOa81vhr5CrRval6i7Tm1qnPkrnAzfyJ2-1EZmAb-FimRQCWLFAM24CvIXchcT4VRSvqFJQGXtE-3n-CFP2j3mayIM029v4llQxGLoheMAeyULHByJUl29mwRPO13VKDAkCI)

## Verificar tabelas do usuário padrão

![](https://lh7-us.googleusercontent.com/8Gwaz9x3beB2-KozHWDOVFAXzQ9nGFJcaeXnTlffHaLUke4qFBlNwA3RW2I4iHD76DYEXzPf4FxnkhK16RKmku9oFMpiS9QK2wTXC-_cw35jkQZkDHDEVkVT3FXJjzeN_ZT3EduykSWxSId5j9RR_Nc)

## Definir permissões no banco de dados

-   Permitir acesso às colunas “nmdep” e “dtnasc” na tabela “tbdep”
	> GRANT SELECT ON OBJECT::tbdep(nmdep, dtnasc) TO TesteBDII;

![](https://lh7-us.googleusercontent.com/OVAxzyIV89pYk6qUFWD6R4rwbIewdw1TLjET9PJ4HR2QpUGNCPk2ZA8DfPd9NGHxK2CXiXxq5eC-IvN-01JGcswIZj5hI1LUszNty3OWtCozav6MkRC01Y6mfARJA0TEjqGlt5BsVuLVQuw2YhZ-Nbo)

## Conectar-se com o Novo Usuário

![](https://lh7-us.googleusercontent.com/SkjOPw1XE67ThGhTg-2LJ92xCM9MQySXwuzCnh3smbngoK3KR588C7Dto1knMR1_HJWwO74olWP2t4cqF9dc7Js3wVzTYpsObW_eS9P41VsligjUEClHcBqSfGhgO8Qk8OcKFjawxrJeMDh1BThE-zc)

## Verificar tabelas do novo usuário (TesteBDII)

![](https://lh7-us.googleusercontent.com/UVvo9cXo9xuToukOuraMQHCtb1vK8Pakh-uy3u6WLZHDaGecuyVYH4JuM41ygb3IcNg1a8QgZm5AuXGw2uvSLdXa_USPkFGm5x1HsnQV8zBizvCQzeCWzu1hcL0r3bmwWhv-QHK6CEuiv7Ep3Ioxm7w)

## Tentativa de consulta de todas as colunas da tabela (tbdep)

![](https://lh7-us.googleusercontent.com/vYwP7tRHdcUhgQ_cjlahZBBK1YO27H1i_Q3uF2u1TWRMLYXEREtSKWPYMjT22dwedeNE4sAS-rT-JX2K3kZa8HUJR9yxm9jG9RjX-Wk9F12pusytyfoN7J7Pwae9WxFct8G37AFLEu-Lloql5wcw3R8)

## Consulta somente das colunas autorizadas na tabela

-   Conectar-se ao banco
	> USE AulaDB;

-   Selecionar as colunas “nmdep” e “dtnasc” da tabela “tbdep”
	>SELECT nmdep, dtnasc FROM tbdep;

![](https://lh7-us.googleusercontent.com/ujxgFd3cPOqgERVeWsaJSlpWneHZF_xBscFStY6ZQLzCvI0mU00RFZ9JozpK9nXICV76ooEDmHvE9d3Cv7s8q4AfG8ei1cJPXaiPckPAbv5mR1Fi5gEVY_9HVGqRRnPifkZzYYAmd2bj1oH9lcViQB4)

## Logar no usuário padrão

![](https://lh7-us.googleusercontent.com/0LqtSb3Bp-KedqgpXMSkYWBhtaUHVQw4eVBISY6hv4lCT3CNZuBHRyajI_ZEL-uv5Eh448TKC7WJNWcTP8BVcNZ0PF9FftXixn7EP4Nq-Ftxm2z8rcJodL8_hXyZm7wurhmaOO0pIXDXFmDQlFtJ-5c)

## Revogar/retirar permissão de acesso à coluna
	> REVOKE SELECT ON OBJECT::tbdep(nmdep, dtnasc) FROM TesteBDII;

![](https://lh7-us.googleusercontent.com/Z3Pw7ssKGWs3x--luDvXtSfv8YxSiND_5RPWXFJIBHyC4XvS1OR3O8XmIMZhZwUoxCy3eU9Bf98vUUeoIDJjHKB3mnMcSiFRnThASkIAvNwIRJOhNHlwEDUOIt8Ki6XoOIZn-h-dpZlegRnYMpO5v1E)

  ## Conectar-se novamente com o outro usuário (TesteBDII)

![](https://lh7-us.googleusercontent.com/SkjOPw1XE67ThGhTg-2LJ92xCM9MQySXwuzCnh3smbngoK3KR588C7Dto1knMR1_HJWwO74olWP2t4cqF9dc7Js3wVzTYpsObW_eS9P41VsligjUEClHcBqSfGhgO8Qk8OcKFjawxrJeMDh1BThE-zc)

## Tentar novamente acessar as colunas anteriormente autorizadas

-   Conectar-se ao banco
	> USE AulaDB;

-   Selecionar as colunas “nmdep” e “dtnasc” da tabela “tbdep”
	> SELECT nmdep, dtnasc FROM tbdep;

![](https://lh7-us.googleusercontent.com/B4l34LwKUB_cvZ0lNrj83gJo-UhGLEywTcgtHvvyw2Is7r_culKDVJq-t1nMPnEgjQC-KLKbshMIqEMFGAcC1IIHrS27uDdF5zYfHRx6SChz3aqN5di9z7mYgYT8KcNCeMUqNkySTkapu0OTuXvIzEk)

  ## Verificar tabelas com permissão no novo usuário

![](https://lh7-us.googleusercontent.com/KtY74lg1ZYK-I6i6sI7e0dl1zRCdWosFkQz429o-fr2JkaCRgvM6qB_utVu6t86A55XLmc5blPT3OSWviqTfqKHAOUyPpJdov8aGzL_-ohlQNJAJ7a6KOqHq8pUQBIFiZyK2FM8stUORxrTzkUqJowo)

  ## Logar novamente no usuário padrão

![](https://lh7-us.googleusercontent.com/0LqtSb3Bp-KedqgpXMSkYWBhtaUHVQw4eVBISY6hv4lCT3CNZuBHRyajI_ZEL-uv5Eh448TKC7WJNWcTP8BVcNZ0PF9FftXixn7EP4Nq-Ftxm2z8rcJodL8_hXyZm7wurhmaOO0pIXDXFmDQlFtJ-5c)

  ## Remover/excluir usuário criado

-   Conectar-se ao banco
	> USE AulaDB;

-   Remover usuário
	> DROP USER TesteBDII;

![](https://lh7-us.googleusercontent.com/DjDo-PgTbe6P51UhR1SfilimrVrzyqzDKBe08eNujjEm5nBD25h1n-r4WTmMp8zvmgodqnFvrp7BKaA4CAeA0ofyXbsO555APLlC4tMdw7HuDGQ0kNVoyZ_9TGzuO6XE8ldIZMcIeXehhYxhLBLpXFM)

## Remover/excluir login no servidor

-   Entrar no Master
	> USE master;

-   Conectar-se à sessão (não constará nada, pois já foi desconectado)
	> SELECT session_id FROM sys.dm_exec_sessions WHERE login_name = 'TesteBDII';

![](https://lh7-us.googleusercontent.com/cnaGNpJYINo6mvu881eXGauoKVXNC752FRdJvOy1nYWk2nxyy0iUMfqA4rFSFjPwJ7ZkrAbw_YANpmuwVZSbTqyiSWrmL7BWUheWkd3QnqeieURcu9G0fDpl6tVptn7cE2lvhTIYSOSKADvJlRTch04)

-   Remover usuário
	> DROP LOGIN TesteBDII;

![](https://lh7-us.googleusercontent.com/935Rp4978UHYouZfFlX4rHi1wX0h2I5Y9kWdTOEZtJ5EaO05lL3C0ggmPMGbF5jxcRMPQBPpwX5IHNrZ4xenvvxr0zfkkwYbOC7Zz4dEtW5yauOFzM-zr5bsKi11HE5slidVSiM75--bhvTFbbTS5KM)
