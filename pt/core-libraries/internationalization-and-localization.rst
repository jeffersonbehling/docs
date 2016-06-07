Internacionalização e Localização
#################################

Uma das melhores maneiras para uma aplicação que permite alcançar uma maior
audiência é para atender a vários idiomas. Isso muitas vezes pode provar
ser uma tarefa difícil, mas a internacionalização e
recursos de localização do CakePHP tornam muito mais fácil .

Primeiro, é importante entender a terminologia.
*Internationalização* refere-se a capacidade de uma aplicação que permite ser localizada.O termo *localização* refere-se à 
adaptação de uma aplicação para atender aos requisitos de idioma específico (ou cultura ) (isto é, uma "localidade"). 
Internacionalização e localização são abreviadas como i18n (internationalization) e l10n (localization), respectivamente; 18 e 10
são o número de caracteres entre o primeiro e último caracteres.

Configurando Traduções
======================

Existem apenas alguns passos para ir de um aplicativo de um único idioma
a uma aplicação multi - lingual , o primeiro dos quais é fazer uso
da função :php:func: `__()` em seu código. Abaixo está um exemplo de algum código
para uma aplicação de um único idioma::

    <h2>Popular Articles</h2>

Para internacionalizar seu código, tudo que você precisa fazer é Refatorar
Strings com :php:func: `__()` por exemplo::

    <h2><?= __('Popular Articles') ?></h2>
    
Fazendo nada mais, estes dois exemplos de código são funcionalmente
idênticos - ambos irão enviar o mesmo conteúdo para o navegador.
A função : php : func: `__()` irá traduzir a string passada se a tradução estiver disponível, ou irá devolvê-la inalterada.

Arquivo de Idiomas
-------------------

Traduções podem ser disponibilizados usando arquivos de idiomas armazenados no
aplicação. O formato padrão para arquivos de tradução do CakePHP é o formato
`Gettext <http://en.wikipedia.org/wiki/Gettext>`_. Os arquivos devem ser
colocado dentro do diretório **src/Locale/** e dentro deste diretório, deve haver
uma subpasta para cada idioma, por exemplo::

 /src
        /Locale
            /en_US
                default.po
            /en_GB
                default.po
                validation.po
            /es
                default.po
                
O domínio padrão é 'default', portanto, a pasta locale deve pelo menos
conter o arquivo **default.po** como mostrado acima. Um domínio refere-se a qualquer arbitrário
agrupamento de mensagens de tradução. Quando nenhum grupo é usado, em seguida, o grupo padrão
é selecionado.

As mensagens de Strings do core extraídos da biblioteca CakePHP pode ser armazenado
separadamente em um arquivo chamado **cake.po** em **src/Locale/**.
O `CakePHP localized library <https://github.com/cakephp/localized>`_ tem as
traduções para as mensagens traduzidas voltados para o cliente no core (o domínio cake). Para usar esses arquivos, baixar ou 
copiá-los para o seu local esperado:
**src/Locale/<locale>/cake.po**. Se sua localidade está incompleta ou incorreta,
por favor envie um PR neste repositório para corrigi-lo.

Plugins também podem conter arquivos de tradução, a convenção é usar o
``under_scored`` no nome do plugin como o domínio para a tradução
mensagens::
