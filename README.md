nfe_utils
-
Biblioteca para gerar pdf da DANFE (retrato e paisagem), DACCe a partir de xml's.

Dependências:

- FPDF2
(pip install fpdf2)

Roadmap
-
- Testes unitários
- Implementar DACTe
- Documentação



Exemplos de uso
-

```
from pdf_docs import Danfe, DaCCe

# DANFE
# cfg_layout -> 3 posibilidades de layout das colunas dos itens no modo retrato: 'ICMS_ST', 'ICMS_ST', 'ICMS_IPI'
# receipt_pos -> impressão do recibo de entrega no topo da DANFE ('top') ou no rodapé ('bottom')

xmls = [open( "xml_nfe.xml", "r", encoding="utf8").read()]
pdf = Danfe(xmls=xmls, image=None, cfg_layout='ICMS_ST', receipt_pos='top')
pdf.output('danfe.pdf', 'F')

# DaCCe
emitente = {'nome': 'COMPANY ME-EPP',
            'end': 'AV TEST, 00',
            'bairro' : 'TEST',
            'cep': '00000-000',
            'cidade': 'SÃO PAULO',
            'uf': 'SP',
            'fone': '(11) 1234-5678'}


xmls = [open( "xml_cce.xml", "r", encoding="utf8").read(),]     
pdf_cce = DaCCe(xmls=xmls, emitente=emitente, image=None)
pdf_cce.output('cce.pdf', 'F')


```
