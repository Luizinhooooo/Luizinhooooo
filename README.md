- class CanalComunicacao:
    def __init__(self, destinatario):
        self.destinatario = destinatario

    def enviar_mensagem(self, mensagem):
        pass  # Implementação genérica para enviar mensagem


class CanalTelefone(CanalComunicacao):
    def enviar_mensagem(self, mensagem):
        print(f"Enviando mensagem para o número {self.destinatario}: {mensagem}")


class CanalUsuario(CanalComunicacao):
    def enviar_mensagem(self, mensagem):
        print(f"Enviando mensagem para o usuário {self.destinatario}: {mensagem}")


class Mensagem:
    def __init__(self, conteudo, data_envio):
        self.conteudo = conteudo
        self.data_envio = data_envio

    def enviar(self, canal):
        pass  # Implementação genérica para enviar mensagem


class MensagemTexto(Mensagem):
    def enviar(self, canal):
        canal.enviar_mensagem(f"Texto: {self.conteudo}, Enviado em: {self.data_envio}")


class MensagemVideo(Mensagem):
    def __init__(self, conteudo, data_envio, arquivo, formato, duracao):
        super().__init__(conteudo, data_envio)
        self.arquivo = arquivo
        self.formato = formato
        self.duracao = duracao

    def enviar(self, canal):
        canal.enviar_mensagem(f"Vídeo: {self.conteudo}, Enviado em: {self.data_envio}, Arquivo: {self.arquivo}, Formato: {self.formato}, Duração: {self.duracao}")


class MensagemFoto(Mensagem):
    def __init__(self, conteudo, data_envio, arquivo, formato):
        super().__init__(conteudo, data_envio)
        self.arquivo = arquivo
        self.formato = formato

    def enviar(self, canal):
        canal.enviar_mensagem(f"Foto: {self.conteudo}, Enviado em: {self.data_envio}, Arquivo: {self.arquivo}, Formato: {self.formato}")


class MensagemArquivo(Mensagem):
    def __init__(self, conteudo, data_envio, arquivo, formato):
        super().__init__(conteudo, data_envio)
        self.arquivo = arquivo
        self.formato = formato

    def enviar(self, canal):
        canal.enviar_mensagem(f"Arquivo: {self.conteudo}, Enviado em: {self.data_envio}, Arquivo: {self.arquivo}, Formato: {self.formato}")


# Exemplo de uso
whatsapp = CanalTelefone("+1234567890")
telegram = CanalUsuario("@usuario_telegram")

mensagem_texto = MensagemTexto("Olá, mundo!", "01/12/2023")
mensagem_video = MensagemVideo("Vídeo de apresentação", "01/12/2023", "video.mp4", "MP4", "5 minutos")
mensagem_foto = MensagemFoto("Imagem legal", "01/12/2023", "imagem.jpg", "JPEG")
mensagem_arquivo = MensagemArquivo("Documento importante", "01/12/2023", "documento.pdf", "PDF")

mensagem_texto.enviar(whatsapp)
mensagem_video.enviar(telegram)
mensagem_foto.enviar(whatsapp)
mensagem_arquivo.enviar(telegram)

