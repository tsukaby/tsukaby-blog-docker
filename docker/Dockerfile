FROM wordpress:4.9.7

ENV WORDPRESS_DB_HOST mydbinstance.cfrtxetqlrkd.ap-northeast-1.rds.amazonaws.com:3306
ENV WORDPRESS_DB_USER root
ENV WORDPRESS_DB_PASSWORD mypassword
ENV WORDPRESS_DB_NAME blog

# Install tools
RUN apt-get update
RUN apt-get -y --force-yes -o Dpkg::Options::="--force-confdef" install wget curl unzip python python-pip
RUN pip install awscli

# Install plugins
WORKDIR /tmp/wp-plugins
RUN wget https://downloads.wordpress.org/plugin/svg-support.2.3.15.zip
RUN wget https://downloads.wordpress.org/plugin/crayon-syntax-highlighter.zip
RUN wget https://downloads.wordpress.org/plugin/easy-fancybox.zip
RUN wget https://downloads.wordpress.org/plugin/google-analytics-for-wordpress.7.0.9.zip
RUN wget https://downloads.wordpress.org/plugin/google-sitemap-generator.4.0.9.zip
RUN wget https://downloads.wordpress.org/plugin/php-text-widget.zip
RUN wget https://downloads.wordpress.org/plugin/tinymce-advanced.4.7.11.zip
RUN wget https://downloads.wordpress.org/plugin/wp-multibyte-patch.2.8.1.zip
RUN wget https://downloads.wordpress.org/plugin/amazon-web-services.zip
RUN wget https://downloads.wordpress.org/plugin/amazon-s3-and-cloudfront.1.4.2.zip
RUN wget https://downloads.wordpress.org/plugin/jetpack.6.3.2.zip

RUN unzip './*.zip' -d /usr/src/wordpress/wp-content/plugins

# Download lang files
WORKDIR /usr/src/wordpress/wp-content/
RUN wget https://s3-ap-northeast-1.amazonaws.com/tsukaby.blog/languages.zip
RUN unzip languages.zip && rm languages.zip


# Change owner
RUN chown -R www-data:www-data /usr/src/wordpress/wp-content

WORKDIR /var/www/html
