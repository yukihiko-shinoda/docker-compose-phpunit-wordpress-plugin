ARG TAG_PHP_UNIT_WORDPRESS_PLUGIN=latest
FROM futureys/phpunit-wordpress-plugin:${TAG_PHP_UNIT_WORDPRESS_PLUGIN}
RUN apt-get update && apt-get install -y nodejs npm && npm install -g @anthropic-ai/claude-code
