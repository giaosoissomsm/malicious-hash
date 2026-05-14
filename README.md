# malicious-hash

Este projeto fornece uma agregação de hashes maliciosos de arquivos (SHA256), destinada à integração com produtos de segurança. As listas são formatadas para fácil consumo por ferramentas como firewalls Fortinet FortiGate, soluções de Endpoint Detection and Response (EDR) e outras plataformas de inteligência contra ameaças.

## Sobre os Hashes

O repositório contém listas de hashes SHA256 correspondentes a malwares conhecidos. Essas listas são mantidas para ajudar administradores e sistemas de segurança a bloquearem ameaças automaticamente.

A principal lista de hashes é:

- `full-hash-sha256-aa.txt`

## Como Utilizar

Você pode utilizar a URL bruta (raw) do arquivo para integrar esta lista como um feed externo de ameaças em seus appliances e soluções de segurança. Cada linha do arquivo contém um único hash SHA256.

### URL raw da lista de hashes

```txt
https://raw.githubusercontent.com/giaosoissomsm/malicious-hash/main/full-hash-sha256-aa.txt
```

## Exemplo de Integração com Fortinet FortiGate

Para utilizar esta lista como um conector externo/feed de ameaças para bloqueio de arquivos em um firewall FortiGate:

1. Acesse o FortiGate e navegue até **Security Fabric > External Connectors**.
2. Clique em **Create New**.
3. Em **Threat Feeds**, selecione **Malware Hash**.
4. No painel de configuração:
   - Defina um **Nome** para o feed (exemplo: `Malicious-Hash-List`).
   - Cole a URL raw abaixo no campo **URI of file**:

   ```txt
   https://raw.githubusercontent.com/giaosoissomsm/malicious-hash/main/full-hash-sha256-aa.txt
   ```

   - Configure o intervalo de atualização desejado (exemplo: a cada 5 minutos).

5. Clique em **OK** para salvar o conector.
6. Navegue até **Security Profiles > AntiVirus**.
7. Edite o perfil aplicado às políticas de segurança.
8. Habilite a opção **Use External Malware Block List** e selecione o feed criado.
9. Salve o perfil AntiVirus.

O FortiGate irá baixar automaticamente a lista de hashes e bloquear arquivos que correspondam aos hashes informados durante a inspeção do tráfego.

## Licença

Este projeto está licenciado sob a licença MIT. Consulte o arquivo [LICENSE](LICENSE) para mais detalhes.
