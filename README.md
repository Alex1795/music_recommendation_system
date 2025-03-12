# Music Recommendation System

An AI-powered music recommendation engine that analyzes audio characteristics to suggest similar songs using Python and Elasticsearch.

## Overview

This project implements a content-based music recommendation system that uses deep learning to generate embeddings from audio files and leverages Elasticsearch's k-Nearest Neighbors (kNN) search to find similar songs based on their acoustic properties.

## How It Works

1. Loads MP3 files using the librosa library
2. Generates 2048-dimensional embeddings using panns_inference.AudioTagging model
3. Normalizes embeddings for consistent comparison
4. Extracts metadata (artist, album, title) from MP3 files
5. Stores songs with their embeddings in Elasticsearch
6. Performs kNN searches to find similar songs based on audio characteristics

You need to provide a Elasticsearch CLOUD ID and API KEY as well as the mp3 files on a dataset/ directory


## System Architecture

```
MP3 Song -> librosa -> Audio Data -> panns_inference -> Embeddings -> Normalize
                    |                                                    |
                    v                                                    v
               Extract Metadata  --------------------------------> Create Document
                    |                                                    |
                    v                                                    v
               Artist, Album, Title                               Upload to Elasticsearch
                                                                         |
                                                                         v
                                                                 Get Random Seed Song
                                                                         |
                                                                         v
                                                                  Run kNN Search
                                                                         |
                                                                         v
                                                               Get the top 3 Similar Songs
```