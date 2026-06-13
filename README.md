# Awesome Compression [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

A curated list of awesome compression and decompression algorithms, libraries, tools, and resources.

Data compression is the process of encoding information using fewer bits than the original representation. It is a fundamental concept in computer science and information theory, enabling efficient storage and transmission of data.

---

## 📑 Contents

- [🧠 Fundamentals](#-fundamentals)
  - [Theory and Basics](#theory-and-basics)
  - [Seminal Papers](#seminal-papers)
- [📉 Algorithms & Formats](#-algorithms--formats)
  - [General Purpose Algorithms](#general-purpose-algorithms)
  - [Algorithm Comparisons](#algorithm-comparisons)
  - [Media Compression](#media-compression)
  - [Integer and Database Compression](#integer-and-database-compression)
  - [Specialized Compression](#specialized-compression)
  - [Columnar and Big Data](#columnar-and-big-data)
- [🤖 Ecosystem (AI/ML)](#-ecosystem-aiml)
  - [Neural Compression](#neural-compression)
  - [Model Compression (ML Efficiency)](#model-compression-ml-efficiency)
- [🛠️ Implementations](#-implementations)
  - [Libraries and Tools](#libraries-and-tools)
  - [Hardware Acceleration](#hardware-acceleration)
- [📊 Analysis & Testing](#-analysis--testing)
  - [Benchmarking](#benchmarking)
  - [Datasets and Corpora](#datasets-and-corpora)
- [📚 Learning & Resources](#-learning--resources)
  - [Books](#books)
  - [Courses and Tutorials](#courses-and-tutorials)
  - [Visualizations and Demos](#visualizations-and-demos)
  - [Journals and Publications](#journals-and-publications)
  - [Engineering Blogs](#engineering-blogs)
  - [Blogs and Web Resources](#blogs-and-web-resources)
  - [Community and Conferences](#community-and-conferences)

---

## 🧠 Fundamentals

### Theory and Basics
*Foundational concepts in information theory and data compression.*

- **[Information Theory (Shannon)](https://en.wikipedia.org/wiki/Information_theory)** - The mathematical study of the quantification, storage, and communication of information.
- **[Kolmogorov Complexity](https://en.wikipedia.org/wiki/Kolmogorov_complexity)** - The length of the shortest computer program that produces the object as output.
- **[Lossless vs. Lossy Compression](https://en.wikipedia.org/wiki/Data_compression)** - The two main categories of data compression techniques.
- **[Burrows-Wheeler Transform (BWT)](https://en.wikipedia.org/wiki/Burrows%E2%80%93Wheeler_transform)** - A data transformation algorithm that rearranges characters into runs, essential for block-sorting compressors (like bzip2).
- **[Move-to-Front Transform (MTF)](https://en.wikipedia.org/wiki/Move-to-front_transform)** - An encoding of data designed to improve the performance of entropy encoding techniques.
- **[Prediction by Partial Matching (PPM)](https://en.wikipedia.org/wiki/Prediction_by_partial_matching)** - An adaptive statistical data compression technique based on context modeling.
- **[Context Mixing](https://en.wikipedia.org/wiki/Context_mixing)** - A type of compression where predictions from multiple independent models are combined (e.g., PAQ).
- **[The Hitchhiker's Guide to Compression](https://github.com/encode/hitchhikers-guide-to-compression)** - A comprehensive guide and repository of lossless compression algorithms.

### Seminal Papers
*The theoretical foundations of modern compression.*

- **[A Mathematical Theory of Communication (1948)](https://people.math.harvard.edu/~ctm/home/text/others/shannon/entropy/entropy.pdf)** - Claude Shannon's foundational paper on information theory.
- **[A Method for the Construction of Minimum-Redundancy Codes (1952)](http://compression.ru/download/articles/huff/huffman_1952_minimum-redundancy-codes.pdf)** - David A. Huffman's paper introducing Huffman coding.
- **[A Universal Algorithm for Sequential Data Compression (1977)](https://ieeexplore.ieee.org/document/1055714)** - Jacob Ziv and Abraham Lempel (LZ77).
- **[Compression of Individual Sequences via Variable-Rate Coding (1978)](https://ieeexplore.ieee.org/document/1055934)** - Jacob Ziv and Abraham Lempel (LZ78).
- **[A Technique for High-Performance Data Compression (1984)](https://courses.cs.duke.edu/spring03/cps296.5/papers/welch_1984_technique_for.pdf)** - Terry Welch (LZW refinement).
- **[Asymmetric Numeral Systems (2013)](https://arxiv.org/abs/1311.2540)** - Jarek Duda's paper introducing ANS, the engine for modern compressors like Zstd and LZFSE.

---

## 📉 Algorithms & Formats

### General Purpose Algorithms
*Algorithms used for lossless data compression, applicable to any data.*

#### Entropy Coding
- **[Huffman Coding](https://en.wikipedia.org/wiki/Huffman_coding)** - An optimal prefix code commonly used for lossless data compression.
- **[Arithmetic Coding](https://en.wikipedia.org/wiki/Arithmetic_coding)** - A form of entropy encoding that encodes the entire message into a single number.
- **[Asymmetric Numeral Systems (ANS)](https://en.wikipedia.org/wiki/Asymmetric_numeral_systems)** - A family of entropy coding methods combining the speed of Huffman with the ratio of Arithmetic coding.
- **[Finite State Entropy (FSE)](https://github.com/Cyan4973/FiniteStateEntropy)** - A fast entropy coder based on ANS, used in Zstd.

#### Dictionary Coders
- **[LZ77 and LZ78](https://en.wikipedia.org/wiki/LZ77_and_LZ78)** - Dictionary-based lossless data compression algorithms published by Lempel and Ziv.
- **[LZW (Lempel-Ziv-Welch)](https://en.wikipedia.org/wiki/Lempel%E2%80%93Ziv%E2%80%93Welch)** - A universal lossless data compression algorithm widely used in GIF.
- **[Deflate](https://en.wikipedia.org/wiki/Deflate)** - A combination of LZ77 and Huffman coding (used in ZIP, gzip, and PNG).

#### Modern Algorithms
- **[LZMA (Lempel-Ziv-Markov chain algorithm)](https://en.wikipedia.org/wiki/Lempel%E2%80%93Ziv%E2%80%93Markov_chain_algorithm)** - High compression ratio algorithm used in the 7z format.
- **[Brotli](https://github.com/google/brotli)** - Optimized for web content and text, developed by Google.
- **[Zstandard (zstd)](https://github.com/facebook/zstd)** - Fast lossless compression targeting real-time scenarios, developed by Facebook.
- **[Snappy](https://github.com/google/snappy)** - Aimed at very high speeds and reasonable compression (Google).
- **[LZ4](https://github.com/lz4/lz4)** - Extremely fast compression algorithm (> 500 MB/s per core).
- **[Oodle](http://www.radgametools.com/oodle.htm)** - A family of high-performance proprietary compressors widely used in gaming (now owned by Epic Games).

### Algorithm Comparisons
*A brief guide on when to use which general-purpose compressor.*

| Algorithm | Focus | Compression Ratio | Speed (Compress/Decompress) | Primary Use Case |
| :--- | :--- | :---: | :---: | :--- |
| **LZ4** | Real-time Speed | Low | Very Fast / Very Fast | In-memory databases, OS kernels, real-time logging. |
| **Snappy** | Speed / Balance | Low-Medium | Very Fast / Very Fast | RPC payloads, Big Data (Hadoop, Parquet). |
| **Zstandard (zstd)** | High Balance | High | Fast / Fast | General replacement for zlib/gzip. Excellent scaling. |
| **Brotli** | Text / Web | High | Slow / Fast | HTTP web compression (HTML, CSS, JS, Fonts). |
| **Gzip (zlib/Deflate)** | Legacy Standard | Medium | Medium / Medium | Legacy web, general file archives (`.tar.gz`). |
| **LZMA (xz, 7-zip)** | Max Compression | Very High | Very Slow / Medium | Software distribution, cold storage archiving. |

### Media Compression
*Algorithms and standards specifically designed for images, audio, and video.*

#### Image
- **[JPEG](https://jpeg.org/jpeg/)** - The industry standard lossy compression for digital images.
- **[PNG](https://en.wikipedia.org/wiki/Portable_Network_Graphics)** - Standard lossless raster-graphics format.
- **[WebP](https://developers.google.com/speed/webp)** - Lossy and lossless format for the web developed by Google.
- **[AVIF](https://aomediacodec.github.io/av1-avif/)** - Next-generation format based on the AV1 video codec. Excellent for web graphics.
- **[JPEG XL](https://jpeg.org/jpegxl/)** - Modern royalty-free raster-graphics format designed for longevity and smooth upgrade from JPEG.
- **[BPG (Better Portable Graphics)](https://bellard.org/bpg/)** - High-efficiency image format based on HEVC.

#### Audio
- **[MP3](https://en.wikipedia.org/wiki/MP3)** - Ubiquitous lossy audio format.
- **[AAC](https://en.wikipedia.org/wiki/Advanced_Audio_Coding)** - Successor to MP3, used in most modern streaming.
- **[FLAC](https://xiph.org/flac/)** - Standard for lossless audio compression.
- **[Opus](https://opus-codec.org/)** - Versatile, low-latency royalty-free codec for speech and music (replaces Speex, Vorbis).
- **[WavPack](https://www.wavpack.com/)** - Hybrid lossless/lossy audio compression standard.

#### Video
- **[H.264 / AVC](https://en.wikipedia.org/wiki/Advanced_Video_Coding)** - The most widely used video standard in the world.
- **[H.265 / HEVC](https://en.wikipedia.org/wiki/High_Efficiency_Video_Coding)** - Successor to H.264 offering much better efficiency.
- **[AV1](https://aomedia.org/av1/)** - Open, royalty-free video codec designed for the web.
- **[VVC (Versatile Video Coding)](https://en.wikipedia.org/wiki/Versatile_Video_Coding)** - The latest H.266 standard.
- **[EVC (Essential Video Coding)](https://en.wikipedia.org/wiki/Essential_Video_Coding)** - An ISO/IEC standard with a royalty-free subset.

### Integer and Database Compression
*Lightweight techniques for compressing columns of integers and structured data.*

- **[Bit-Packing](https://en.wikipedia.org/wiki/Bit-packing)** - Storing integers using the minimum number of bits required.
- **[Frame of Reference (FOR)](https://en.wikipedia.org/wiki/Frame_of_Reference_encoding)** - Storing values as offsets from a base value.
- **[PForDelta](https://en.wikipedia.org/wiki/PFOR)** - Patched Frame Of Reference, handles outliers efficiently.
- **[TurboPFor](https://github.com/powturbo/TurboPFor-Integer-Compression)** - Extremely fast integer compression library using SIMD.
- **[FastPFor](https://github.com/lemire/FastPFor)** - A C++ library for fast integer compression using SIMD.
- **[StreamVByte](https://github.com/lemire/streamvbyte)** - A SIMD-accelerated variable-byte encoding.

### Specialized Compression
*Techniques adapted for specific types of data.*

- **[Time Series Data Compression](https://www.timescale.com/blog/time-series-compression/)** - Specialized techniques like Facebook's Gorilla.
- **[Genomic Compression](https://en.wikipedia.org/wiki/DNA_data_compression)** - Specialized formats for DNA sequence data like CRAM.
- **[Mesh Compression](https://google.github.io/draco/)** - Google Draco for compressing 3D geometric meshes and point clouds.
- **[Executable Compression (UPX)](https://upx.github.io/)** - The Ultimate Packer for eXecutables.
- **[CLP (Compressed Log Processor)](https://github.com/y-scope/clp)** - Tool for high-ratio log compression and fast searching.

### Columnar and Big Data
- **[Apache Parquet](https://parquet.apache.org/)** - Columnar storage format with advanced encoding and compression.
- **[Apache ORC](https://orc.apache.org/)** - High-performance columnar storage for Hadoop workloads.
- **[BtrBlocks](https://github.com/db-tu/btrblocks)** - A high-throughput columnar compression format.

---

## 🤖 Ecosystem (AI/ML)

### Neural Compression
*Machine learning based codecs for high-efficiency media compression.*

- **[CompressAI](https://github.com/InterDigitalInc/CompressAI)** - A PyTorch research library and evaluation platform.
- **[NeuralCompression](https://github.com/facebookresearch/NeuralCompression)** - Meta AI's repository for neural compression research.
- **[EnCodec](https://github.com/facebookresearch/encodec)** - High-fidelity neural audio codec from Meta.
- **[DAC (Descript Audio Codec)](https://github.com/descriptinc/descript-audio-codec)** - High-quality universal audio tokenizers.
- **[TensorFlow Compression](https://github.com/tensorflow/compression)** - Google's library for learned data compression.

### Model Compression (ML Efficiency)
*Techniques to reduce the size of machine learning models.*

- **[Quantization](https://huggingface.co/docs/optimum/concept_guides/quantization)** - Reducing precision of weights (e.g., GPTQ, AWQ, GGUF).
- **[Pruning](https://en.wikipedia.org/wiki/Pruning_(decision_trees))** - Removing redundant parameters from a neural network.
- **[Distillation](https://en.wikipedia.org/wiki/Knowledge_distillation)** - Training a small model to mimic a larger one.
- **[ZipNN](https://github.com/zipnn/zipnn)** - Lossless compression for deep learning tensors.

---

## 🛠️ Implementations

### Libraries and Tools
*Software implementations and language-specific packages.*

#### Command Line Utilities (CLI) & Archivers
- **[7-Zip](https://www.7-zip.org/)** - Open source file archiver with extremely high compression ratios.
- **[pigz](https://zlib.net/pigz/)** - A parallel implementation of gzip for multi-core systems.
- **[pbzip2](https://launchpad.net/pbzip2)** - A parallel implementation of the bzip2 block-sorting compressor.
- **[pxz](https://github.com/jnovy/pxz)** - Parallel LZMA compression for XZ files.
- **[lzop](https://www.lzop.org/)** - A very fast file compressor based on the LZO library.
- **[ZPAQ](http://mattmahoney.net/dc/zpaq.html)** - Incremental journaling archiver using PAQ context mixing.
- **[squashfs-tools](https://github.com/plougher/squashfs-tools)** - Tools for creating highly compressed read-only filesystems.

#### Media Optimization Tools
- **[FFmpeg](https://ffmpeg.org/)** - The Swiss army knife for audio and video processing.
- **[ImageMagick](https://imagemagick.org/)** - Suite for image manipulation and conversion.
- **[libjpeg-turbo](https://libjpeg-turbo.org/)** - SIMD-accelerated JPEG codec.
- **[mozjpeg](https://github.com/mozilla/mozjpeg)** - Mozilla's improved JPEG encoder for smaller file sizes.
- **[pngquant](https://pngquant.org/)** - Lossy PNG compressor using palette quantization.
- **[OxiPNG](https://github.com/shssoichiro/oxipng)** - Fast, multithreaded PNG optimizer written in Rust.
- **[SVGO](https://github.com/svg/svgo)** - Node.js tool for optimizing SVG files.

#### Multi-Language / C / C++
- **[zlib-ng](https://github.com/zlib-ng/zlib-ng)** - Next-generation zlib optimized for modern CPUs.
- **[ISA-L](https://github.com/intel/isa-l)** - Intel's storage acceleration library for extreme performance.
- **[zstd](https://github.com/facebook/zstd)** - Official Zstandard reference implementation.
- **[lz4](https://github.com/lz4/lz4)** - Official LZ4 reference implementation.
- **[C-Blosc](https://github.com/Blosc/c-blosc)** - Optimized library for numerical and structured data.

#### Rust
- **[zlib-rs](https://github.com/trifectatechfoundation/zlib-rs)** - Pure Rust DEFLATE implementation, often faster than C zlib-ng.
- **[lz4-flex](https://github.com/PSeitz/lz4-flex)** - Extremely fast pure Rust LZ4 implementation.
- **[zstd-rs](https://github.com/gyscos/zstd-rs)** - High-quality Rust bindings for Zstandard.
- **[vortex](https://github.com/vortex-data/vortex)** - Modern columnar compression toolkit for Rust.
- **[flate2](https://github.com/rust-lang/flate2-rs)** - Standard Rust DEFLATE library with multiple backends.

#### Go
- **[klauspost/compress](https://github.com/klauspost/compress)** - Highly optimized Go implementations of Zstd and Snappy.
- **[pgzip](https://github.com/klauspost/pgzip)** - Parallel gzip for Go, up to 25x faster.
- **[dsnet/compress](https://github.com/dsnet/compress)** - Collection of compression algorithms for Go.

#### Python
- **[python-zstandard](https://github.com/indygreg/python-zstandard)** - Feature-rich Zstd bindings for Python.
- **[Blosc2](https://github.com/Blosc/python-blosc2)** - Numerical data compressor with compute-on-compressed support.
- **[python-isal](https://github.com/pycompression/python-isal)** - Python bindings for Intel's ISA-L.
- **[python-zlib-ng](https://github.com/pycompression/python-zlib-ng)** - Drop-in replacement for zlib using zlib-ng.

#### Java / JVM
- **[Apache Commons Compress](https://github.com/apache/commons-compress)** - Unified API for many formats (ZIP, TAR, Gzip, Zstd, etc.).
- **[lz4-java](https://github.com/lz4/lz4-java)** - High-speed JNI and pure Java bindings for LZ4.
- **[snappy-java](https://github.com/xerial/snappy-java)** - Fast Snappy compression/decompression for Java.
- **[Zip4j](https://github.com/srikanth-lingala/zip4j)** - Advanced ZIP-specific features (encryption, spanning).

#### JavaScript / TypeScript
- **[fflate](https://github.com/101arrowz/fflate)** - High-performance, tiny pure JS compression library.
- **[pako](https://github.com/nodeca/pako)** - Reliable Zlib port for JS (browser/Node.js).
- **[JSZip](https://github.com/Stuk/jszip)** - Create, read and edit .zip files with Javascript.
- **[lz-string](https://github.com/pieroxy/lz-string)** - Optimized for localStorage string compression.

#### C# / .NET
- **[SharpCompress](https://github.com/adamhathcock/sharpcompress)** - Fully managed library for RAR, 7Zip, Zip, Tar, etc.
- **[EasyCompressor](https://github.com/mjebrahimi/EasyCompressor)** - Unified interface for LZ4, Snappy, Zstd, and more.
- **[K4os.Compression.LZ4](https://github.com/MiloszKrajewski/K4os.Compression.LZ4)** - High-performance LZ4 implementation for .NET.

#### Ruby
- **[ruby-zstd](https://github.com/facebook/zstd/tree/dev/contrib/ruby)** - Official Zstandard bindings for Ruby.
- **[lz4-ruby](https://github.com/komiya-atsushi/lz4-ruby)** - High-speed LZ4 bindings for Ruby.

#### PHP
- **[UnifiedArchive](https://github.com/wapmorgan/UnifiedArchive)** - Abstract API for many archive formats.
- **[ZipStream-PHP](https://github.com/maennchen/ZipStream-PHP)** - Stream ZIP files directly to users without disk storage.

#### Swift / Apple Platforms
- **[SWCompression](https://github.com/tsolomko/SWCompression)** - Pure Swift framework for archives and compression.
- **[DataCompression](https://github.com/mw99/DataCompression)** - Lightweight Swift extensions for data compression.

---

## 🛠️ Implementations

### Hardware Acceleration
*Offloading compression to specialized hardware.*

- **[Intel QuickAssist Technology (QAT)](https://www.intel.com/content/www/us/en/architecture-and-technology/intel-quickassist-technology-overview.html)** - Hardware acceleration for Deflate.
- **[nvCOMP](https://github.com/NVIDIA/nvcomp)** - GPU-accelerated lossless compression from NVIDIA.
- **[AWS Nitro](https://aws.amazon.com/ec2/nitro/)** - Hardware offload for transparent storage compression.

---

## 📊 Analysis & Testing

### Benchmarking
*Tools for comparing compression algorithms.*

- **[lzbench](https://github.com/inikep/lzbench)** - In-memory lossless compression benchmark.
- **[Squash](https://github.com/quixdb/squash)** - Abstraction library and benchmark for lossless compression.
- **[TurboBench](https://github.com/powturbo/TurboBench)** - Comprehensive benchmark for numerous algorithms.

### Datasets and Corpora
*Standard datasets for benchmarking compression algorithms.*

- **[Silesia Corpus](https://sun.aei.polsl.pl//~sdeor/index.php?page=silesia)** - The modern standard for lossless benchmarking (~211 MB).
- **[Canterbury Corpus](https://corpus.canterbury.ac.nz/)** - Collection for general-purpose benchmarking.
- **[Calgary Corpus](http://www.data-compression.info/Corpora/CalgaryCorpus/)** - Historical standard for early research.
- **[ImageNet](https://www.image-net.org/)** - Large-scale dataset used for neural image compression.
- **[LibriSpeech](https://www.openslr.org/12)** - Standard for benchmarking audio and speech codecs.
- **[KITTI](http://www.cvlibs.net/datasets/kitti/)** - Sensor data for point cloud and robotics compression.

---

## 📚 Learning & Resources

### Books
- **[Data Compression: The Complete Reference](https://www.amazon.com/Data-Compression-Reference-David-Salomon/dp/1846286026)** by David Salomon.
- **[Introduction to Data Compression](https://www.amazon.com/Introduction-Data-Compression-Khalid-Sayood/dp/0124157963)** by Khalid Sayood.
- **[Elements of Information Theory](https://www.amazon.com/Elements-Information-Theory-Thomas-Cover/dp/0471241954)** by Cover and Thomas.
- **[Managing Gigabytes](https://www.cs.mu.oz.au/mg/)** by Witten, Moffat, and Bell - Compression and indexing.

### Courses and Tutorials
- **[Data Compression Course (Stanford)](https://web.stanford.edu/class/ee398a/)** - Principles and practice of compression.
- **[Information Theory (Khan Academy)](https://www.khanacademy.org/computing/computer-science/informationtheory)** - Gentle introduction to the theory.
- **[Colt McAnlis' Data Compression Videos](https://www.youtube.com/playlist?list=PLOU2XLYxmsIKWEJoksyYJvXgQ_LhDngb0)** - Engaging series on fundamentals.

### Visualizations and Demos
*Interactive tools to understand how compression works.*

- **[Huffman Coding Visualizer](https://huffman-coding-visualizer-pbxfa.ondigitalocean.app/)** - Build Huffman trees in real-time.
- **[LZ77 Simulator](https://mysimulator.uk/)** - Visualize the sliding window and lookahead buffer.
- **[LZW Interactive Demo](https://csfieldguide.org.nz/en/chapters/data-compression/lzw-compression/)** - See how dictionaries are built.
- **[JPEG Explained](https://pudding.cool/2018/03/compression/)** - A beautiful visual essay on JPEG.
- **[BWT Online Encoder](https://calcoolator.eu/burrows-wheeler-transform-encoder-decoder)** - Step through the BWT.

### Journals and Publications
- **[IEEE Transactions on Information Theory](https://ieeexplore.ieee.org/xpl/RecentIssue.jsp?punumber=18)** - Premier journal for theoretical aspects.
- **[IEEE Transactions on Image Processing](https://ieeexplore.ieee.org/xpl/RecentIssue.jsp?punumber=83)** - Cutting-edge image compression research.
- **[IEEE Transactions on Multimedia](https://ieeexplore.ieee.org/xpl/RecentIssue.jsp?punumber=6046)** - Covers full multimedia systems.
- **[Software: Practice and Experience](https://onlinelibrary.wiley.com/journal/1097024x)** - Practical papers on implementation.

### Engineering Blogs
*Insights into real-world compression at scale from industry leaders.*

- **[Meta Engineering: Compression](https://engineering.fb.com/tag/compression/)** - Home of Zstandard and infrastructure deep-dives.
- **[Cloudflare Blog: Compression](https://blog.cloudflare.com/tag/compression/)** - Low-level network and edge optimizations.
- **[Google Open Source Blog](https://opensource.googleblog.com/)** - News on Brotli, Snappy, and WebP.
- **[Netflix Tech Blog](https://netflixtechblog.com/)** - Video encoding and data warehouse efficiency.
- **[Dropbox Tech Blog](https://dropbox.tech/infrastructure)** - Masters of storage and makers of Lepton.

### Blogs and Web Resources
- **[Matt Mahoney's Data Compression Programs](http://mattmahoney.net/dc/)** - Rich repository of software and benchmarks.
- **[Fast Compression Blog](http://fastcompression.blogspot.com/)** - Yann Collet's blog (LZ4/Zstd creator).
- **[cbloom rants](https://cbloomrants.blogspot.com/)** - Charles Bloom's technical analysis (Oodle creator).
- **[The ryg blog](https://fgiesen.wordpress.com/)** - Fabian Giesen's series on entropy coding.
- **[Compression.ru](http://www.compression.ru/index_en.htm)** - Large resource for video compression.

### Community and Conferences
- **[DCC (Data Compression Conference)](https://datacompressions.com/dcc/)** - The premier academic conference.
- **[PCS (Picture Coding Symposium)](https://picturecodingsymposium.org/)** - Conference focusing on visual media.
- **[ISIT (IEEE ISIT)](https://www.itsoc.org/conferences/isit)** - Flagship information theory symposium.
- **[r/compression](https://www.reddit.com/r/compression/)** - Active Reddit community.
- **[Encode.su](https://encode.su/)** - Forum for compression enthusiasts.

---

## Contributing
Contributions are welcome! Please read the [contribution guidelines](CONTRIBUTING.md) first.
