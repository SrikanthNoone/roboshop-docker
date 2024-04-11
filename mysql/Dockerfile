FROM mysql:5.7

# Set environment variables for MySQL
ENV MYSQL_ALLOW_EMPTY_PASSWORD=yes \
    MYSQL_DATABASE=cities \
    MYSQL_USER=shipping \
    MYSQL_PASSWORD=RoboShop@1

# Copy the SQL dump files into the container's initialization directory
COPY scripts/dump.sql.gz /docker-entrypoint-initdb.d/
COPY scripts/ratings.sql /docker-entrypoint-initdb.d/

# Modify the entrypoint script to decompress the SQL dump file before initializing the database
COPY entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh

# Execute the entrypoint script to start the MySQL server
ENTRYPOINT ["/entrypoint.sh"]
