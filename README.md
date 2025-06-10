# transa-esMYSQL
-- Início da transação
BEGIN;

-- Débito na conta de origem
UPDATE contas SET saldo = saldo - 500 WHERE id = 1;

-- Crédito na conta de destino
UPDATE contas SET saldo = saldo + 500 WHERE id = 2;

-- Confirma as alterações (commit)
COMMIT;
Se algo der errado durante a transação, use ROLLBACK:


mysqldump -u usuario -p nome_do_banco > backup.sql

pg_restore -U usuario -d nome_do_banco -v "backup.bak"

-- Bloquear novas transações
FLUSH TABLES WITH READ LOCK;

-- Executar o backup (ex: via script bash)

-- Desbloquear
UNLOCK TABLES;
#!/bin/bash
DATA=$(date +"%Y-%m-%d_%H-%M")
mysqldump -u root -pminhasenha banco_exemplo > /backups/banco_exemplo_$DATA.sql
