# jlr-formulaire-v2

Assets
cd public
ln -s ../assets/ ./assets
<img src="{{ asset('assets/jaguar/img/bulle_aide.png') }}" alt="Aide" style="cursor:pointer;" />

Generation Pomm 
 bin/console pomm:generate:relation-all -d ./src/Component  -a 'App\Component' application referentiel_satellite public --psr4
 bin/console pomm:generate:relation-all -d ./src/Component  -a 'App\Component' application marque public --psr4
 bin/console pomm:generate:relation-all -d ./src/Component  -a 'App\Component' application modele public --psr4
 bin/console pomm:generate:relation-all -d ./src/Component  -a 'App\Component' application formulaire public --psr4
 bin/console pomm:generate:relation-all -d ./src/Component  -a 'App\Component' application formulaire_type public --psr4
 bin/console pomm:generate:relation-all -d ./src/Component  -a 'App\Component' application modele_visuel public --psr4
 
 bin/console pomm:generate:relation-all -d ./src/Component  -a 'App\Component' application mention_legale formulaire --psr4
 bin/console pomm:generate:relation-all -d ./src/Component  -a 'App\Component' application formulaire_modele formulaire --psr4
 bin/console pomm:generate:relation-all -d ./src/Component  -a 'App\Component' application tag formulaire --psr4
 
 bin/console pomm:generate:relation-all -d ./src/Component  -a 'App\Component' application formulaire_lead historique --psr4
 bin/console pomm:generate:relation-all -d ./src/Component  -a 'App\Component' application lead historique --psr4

=============== Paramétrage =======================

Fichier /etc/hosts
127.0.0.1	v2.contact-jaguar.local
127.0.0.1	v2.contact-landrover.local


Apache => /etc/apache2/sites-available/jlr-form-v2.conf puis sudo a2ensite jlr-form-v2 

<VirtualHost *:80>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        ServerName www.v2.local
        ServerAlias v2.contact-jaguar.local v2.contact-landrover.local

        ServerAdmin lbolzer@sismic.fr
        DocumentRoot /home/laurent/www/eskalad/jlr/jlr-formulaire-v2/public/

        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn

        ErrorLog ${APACHE_LOG_DIR}/jlr-formulaire-v2_error.log
        CustomLog ${APACHE_LOG_DIR}/jlr-formulaire-v2_access.log combined

        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf
</VirtualHost>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet


URL pour accéder au formulaire : 
http://v2.contact-jaguar.local/index.php/demande-essai
http://v2.contact-landrover.local/index.php/demande-essai

Récupérer les sql de 201803 & 201804 & 201805 dans dossier sql/schema du projet infoconcession