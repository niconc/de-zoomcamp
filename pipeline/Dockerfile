FROM python:3.13.15-slim

# Copy the uv binary from the uv image
COPY --from=ghcr.io/astral-sh/uv:latest /uv /bin/

# Current directory
WORKDIR /code
ENV PATH="/code/.venv/bin:$PATH"

# Copy files from pipeline directory to /code in the container
COPY pyproject.toml .python-version uv.lock ./ 
RUN uv sync --locked

COPY pipeline.py .

ENTRYPOINT ["python", "pipeline.py"]

