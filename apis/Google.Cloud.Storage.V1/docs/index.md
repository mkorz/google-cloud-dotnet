# Google.Cloud.Storage.V1

`Google.Cloud.Storage.V1` is a .NET client library for [Google
Cloud Storage](https://cloud.google.com/storage/). It wraps the
`Google.Apis.Storage.v1` generated library, providing a
higher-level API to make it easier to use.

# Installation

Install the `Google.Cloud.Storage.V1` package from NuGet. Add it to
your project in the normal way (for example by right-clicking on the
project in Visual Studio and choosing "Manage NuGet Packages...").
Please ensure you enable pre-release packages (for example, in the
Visual Studio NuGet user interface, check the "Include prerelease"
box).

# Authentication

To authenticate all your API calls, first install and setup the
[Google Cloud SDK](https://cloud.google.com/sdk/). After that is
installed, run the following command in a Google Cloud SDK Shell:

```sh
> gcloud auth application-default login
```

# Getting started

Common operations are exposed via the
[StorageClient](obj/api/Google.Cloud.Storage.V1.StorageClient.yml) class.

# Sample code

[!code-cs[](obj/snippets/Google.Cloud.Storage.V1.StorageClient.txt#Overview)]

## Signed URLs

Signed URLs can be created to provide limited access to specific buckets and
objects to anyone in possession of the URL, regardless of whether they have
a Google account.

For example, Signed URLs can be created to provide read-only access to
existing objects:

[!code-cs[](obj/snippets/Google.Cloud.Storage.V1.UrlSigner.txt#SignedURLGet)]

Or write-only access to put specific object content into a bucket:

[!code-cs[](obj/snippets/Google.Cloud.Storage.V1.UrlSigner.txt#SignedURLPut)]

## Upload URIs

In some cases, it may not make sense for client applications to have permissions
to begin an upload for an object, but an authenticated service may choose to grant
this ability for individual uploads. Signed URLs are one option for this. Another
option is for the service to start a resumable upload session, but instead of
performing the upload, sending the resulting upload URI to the client application
so it can perform the upload instead. Unlike sessions initiated with a signed URL,
a pre-initated upload session will force the client application to upload through
the region in which the session began, which will likely be close to the service,
and not necessarily the client.

[!code-cs[](obj/snippets/Google.Cloud.Storage.V1.StorageClient.txt#UploadObjectWithSessionUri)]

## Customer-supplied encryption keys

Storage objects are always stored encrypted, but if you wish to
specify your own encryption key instead of using the server-supplied
one, you can do so either for all operations with a particular
`StorageClient` or on individual ones.

[!code-cs[](obj/snippets/Google.Cloud.Storage.V1.StorageClient.txt#CustomerSuppliedEncryptionKeys)]
