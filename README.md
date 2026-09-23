Foto → Modelo 3D → STL imprimível (Google Colab)
Versão 4 Uma foto entra, um STL pronto para o fatiador sai, com visualização 3D no próprio notebook e um app web opcional para apresentar ao vivo.

Gerador: Hunyuan3D-2mini (Tencent), só a parte de geometria.

Por que esta versão funciona e as anteriores não
Problema das versões antigas	O que esta faz
TRELLIS precisa de spconv, vox2seq e kernels compilados que não existem para o Python 3.13 do Colab	Nada é compilado: tudo é Python puro + PyTorch que já vem no Colab
TripoSR não é instalável via pip (git clone falhava) e depende de torchmcubes compilado	O pacote hy3dgen é instalado direto do PyPI
Células reinstalavam torch/Pillow e quebravam o ambiente	Nunca mexe no torch; se o pip atualizar Pillow/NumPy, o notebook reinicia sozinho uma vez
Chamadas de API erradas (target_count, argumentos do pymeshfix)	Parte de reparo testada com malhas quebradas
Antes de começar
Ambiente de execução → Alterar o tipo de ambiente de execução → GPU T4 (ou L4).
Importante: como as versões anteriores desinstalaram o PyTorch, comece limpo: Ambiente de execução → Desconectar e excluir ambiente de execução.
Rode as células em ordem, de cima para baixo.
Etapa	T4 (1ª vez)	T4 (depois)
Instalação	~2 min	segundos
Download dos pesos (3,8 GB)	1–3 min	já em disco
Geração 3D (qualidade normal)	~1–2 min	~1–2 min
Reparo + STL	< 30 s	< 30 s
As mensagens vermelhas ERROR: pip's dependency resolver... citando cudf, numba, pytensor etc. são avisos sobre pacotes do Colab que não usamos. Não são o erro. A célula de instalação diz explicitamente se algo realmente falhou.