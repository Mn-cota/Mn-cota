- 👋 Hi, I’m @Mn-cota
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
Mn-cota/Mn-cota is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
Claro! Aqui está um exemplo de código para criar um bot de automação para WhatsApp utilizando a biblioteca "selenium" em Python:

```python
from selenium import webdriver
from selenium.webdriver.common.keys import Keys
import time

# Configurando o navegador
driver = webdriver.Firefox()
driver.get("https://web.whatsapp.com")
time.sleep(10)  # Tempo para fazer o login manualmente através do QR Code

# Função para enviar mensagem
def enviar_mensagem(contato, mensagem):
    try:
        # Pesquisar o contato
        campo_pesquisa = driver.find_element_by_xpath('//div[contains(@class,"copyable-text selectable-text")]')
        campo_pesquisa.click()
        campo_pesquisa.send_keys(contato)
        campo_pesquisa.send_keys(Keys.ENTER)
        time.sleep(2)
        
        # Escrever a mensagem
        campo_mensagem = driver.find_elements_by_xpath('//div[contains(@class,"copyable-text selectable-text")]')
        campo_mensagem[1].click()
        campo_mensagem[1].send_keys(mensagem)
        
        # Enviar a mensagem
        campo_mensagem[1].send_keys(Keys.ENTER)
        time.sleep(2)
        
    except Exception as e:
        print(f"Erro ao enviar mensagem para {contato}: {str(e)}")

# Exemplo de uso
contato = "Nome do Contato"  # Nome exato do contato como aparece no WhatsApp
mensagem = "Olá, este é um exemplo de mensagem automática."
enviar_mensagem(contato, mensagem)

# Fechar o navegador
driver.quit()
```
