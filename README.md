# **Ajustando o Limite de Decisão (Threshold) para Previsão de Classe**

Existem muitas técnicas que podem ser usadas para resolver um problema de classificação desequilibrada, como a reamostragem do conjunto de dados de treinamento e o desenvolvimento de versões personalizadas de algoritmos de aprendizado de máquina. No entanto, talvez a abordagem mais simples para lidar com um grave desequilíbrio de classes seja alterar o limiar de decisão. 


Os modelos de classificação não retornam 0 ou 1, mas sim um valor probabilístico. 
* O **predict_proba** é o método que retorna as estimativas de probabilidade condicionais para cada classe
* O **predict** é o método que faz o ajuste das probabailidades usando o limite de decisão (ou threshold) e assim retorna 0 ou 1. 
* O **threshold** padrão é 0.5, ou seja, se um valor está acima de 0.5 pertence a classe 1, senão a classe 0.


Embora essas regras codificadas possam, à primeira vista, parecer razoáveis ​​como comportamento padrão, elas certamente não são ideais para a maioria dos casos de uso. Vamos ilustrar com um exemplo.

Considere um cenário em que um modelo preditivo está sendo implantado para auxiliar os médicos na detecção de tumores. Neste cenário, os médicos provavelmente estarão interessados ​​em identificar todos os pacientes com câncer e em não perder ninguém com câncer, para que possam fornecer-lhes o tratamento correto. 

Em outras palavras, os médicos priorizam alcançar uma alta taxa de recall. Esta ênfase na recordação vem, naturalmente, com o compromisso de potencialmente mais previsões falso-positivas, reduzindo a precisão do modelo. Este é um risco que os médicos estão dispostos a correr porque o custo de um câncer não detectado é muito mais elevado do que o custo de novos testes de diagnóstico. Consequentemente, quando se trata de decidir se deve ou não classificar um paciente como tendo câncer, pode ser mais benéfico classificá-lo como positivo para câncer quando a estimativa da probabilidade condicional é muito inferior a 0,5.

Uma solução para resolver o problema declarado na introdução é ajustar o limite de decisão do classificador assim que o modelo for treinado.
