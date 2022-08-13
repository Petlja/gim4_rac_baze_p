Пројекција и селекција -- музика
--------------------------------

Прикажимо сада неколико упита над базом која садржи податке компанију
за продају музичких композиција.

.. questionnote::

   Прикажи све називе извођача.

.. code-block:: sql

   SELECT naziv
   FROM izvodjac;

Извршавањем упита добија се следећи резултат:

.. csv-table::
   :header:  "naziv"
   :align: left

   "AC/DC"
   "Accept"
   "Aerosmith"
   "Alanis Morissette"
   "Alice In Chains"
   ...

Уколико упит желимо да тестирамо у систему SQLite Studio, 
потребно је да кликне на креирану базу прозору ``Databases`` и потом изабере команда 
менија ``Tools → Open SQL Editor``. 
Када се напише упит, кликне се на дугме ``Execute query (F9)`` (плави троуглић). 
Како највероватније имамо више база података, обавезно проверити да ли је поред овог 
дугмета назив базе у којој желите да вршите упите.

.. image:: ../../_images/music1.png
   :width: 300
   :align: center

Савет је да се у прозору ``Databases`` увек прво провере тачни називи табела. 

.. image:: ../../_images/music2.png
   :width: 300
   :align: center
 
Често ће нам код упита бити потребно да знамо и тачне називе колона, 
а понекад нам је значајно и да знамо како су неки подаци записани у бази 
(да ли су ћирилична слова, да ли су латинична, да ли имена и називи почињу 
великим словом, итд), па је добро да се пре писања коначног решења задатка 
прво напише и изврши основни ``SELECT`` упит који приказује све податке из табеле.
На следећој слици може да се види упит којим добијамо називе извођача написан 
и покренут у систему SQLite Studio. Види се само првих неколико редова и информација 
о томе да има укупно 275 редова у овој табели. 
 
.. image:: ../../_images/music3.png
   :width: 600
   :align: center
   
   
.. questionnote::

   Прикажи све називе песама са албума чији је идентификатор 1.

.. code-block:: sql

   SELECT naziv
   FROM kompozicija
   WHERE id_album = 1;

Извршавањем упита добија се следећи резултат:

.. csv-table::
   :header:  "naziv"
   :align: left

   "For Those About To Rock (We Salute You)"
   "Put The Finger On You"
   "Let's Get It Up"
   "Inject The Venom"
   "Snowballed"
   ...

.. questionnote::

   Прикажи сва имена и презимена запослених који су из Канаде.

.. code-block:: sql

   SELECT ime, prezime
   FROM zaposleni
   WHERE drzava = 'Canada';

Извршавањем упита добија се следећи резултат:

.. csv-table::
   :header:  "ime", "prezime"
   :align: left

   "Andrew", "Adams"
   "Nancy", "Edwards"
   "Jane", "Peacock"
   "Margaret", "Park"
   "Steve", "Johnson"
   ..., ...


Вежба
.....

Покушај сада самостално да решиш наредних неколико задатака.

.. questionnote::

 Прикажи називе свих албума извођача чији је идентификатор 1.
 
.. dbpetlja:: db_proj_restr_muz_01
   :dbfile: music.sql
   :showresult:
   :solutionquery: SELECT naziv
                   FROM album
                   WHERE id_izvodjac = 1
				   

.. questionnote::

 Прикажи идентификаторе, имена и презимена купаца који се зову ``Jack``.

.. dbpetlja:: db_proj_restr_muz_02
   :dbfile: music.sql
   :showresult:
   :solutionquery:  SELECT id_kupac, ime, prezime
                    FROM kupac
                    WHERE ime = 'Jack'
