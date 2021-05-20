---
title: Rozdział 4 — Opis Azure RTOS NetX Secure
description: Ten rozdział zawiera opis wszystkich usług NetX Secure (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 80ec22058ab64ed0c6258bb3d9364ec44f9a741b
ms.sourcegitcommit: 4ebe7c51ba850951c6a9d0f15e22d07bb752bc28
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2021
ms.locfileid: "110223396"
---
# <a name="chapter-4---description-of-azure-rtos-netx-secure-services"></a><span data-ttu-id="e9bb8-103">Rozdział 4 — Opis Azure RTOS NetX Secure</span><span class="sxs-lookup"><span data-stu-id="e9bb8-103">Chapter 4 - Description of Azure RTOS NetX Secure services</span></span>

<span data-ttu-id="e9bb8-104">Ten rozdział zawiera opis wszystkich bezpiecznego Azure RTOS NetX (wymienionych poniżej) w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-104">This chapter contains a description of all Azure RTOS NetX Secure services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="e9bb8-105">W sekcji "Wartości zwracane" w poniższych  opisach interfejsu API makro NX_SECURE_DISABLE_ERROR_CHECKING używane do wyłączania sprawdzania błędów interfejsu API nie ma wpływu na wartości z pogrubieniem, **natomiast** wartości bez pogrubienia są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_SECURE_DISABLE_ERROR_CHECKING** macro that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- [<span data-ttu-id="e9bb8-106">nx_secure_crypto_table_self_test</span><span class="sxs-lookup"><span data-stu-id="e9bb8-106">nx_secure_crypto_table_self_test</span></span>](#nx_secure_crypto_table_self_test)
  - <span data-ttu-id="e9bb8-107">Wykonywanie self_test na metodach kryptograficznych</span><span class="sxs-lookup"><span data-stu-id="e9bb8-107">Perform self_test on the crypto methods</span></span>
- [<span data-ttu-id="e9bb8-108">nx_secure_module_hash_compute</span><span class="sxs-lookup"><span data-stu-id="e9bb8-108">nx_secure_module_hash_compute</span></span>](#nx_secure_module_hash_compute)
  - <span data-ttu-id="e9bb8-109">Oblicza wartość skrótu przy użyciu user_supplied funkcji skrótu</span><span class="sxs-lookup"><span data-stu-id="e9bb8-109">Computes hash value using user_supplied hash function</span></span>
- [<span data-ttu-id="e9bb8-110">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-110">nx_secure_tls_active_certificate_set</span></span>](#nx_secure_tls_active_certificate_set)
  - <span data-ttu-id="e9bb8-111">Ustawianie aktywnego certyfikatu tożsamości dla bezpiecznej sesji TLS NetX</span><span class="sxs-lookup"><span data-stu-id="e9bb8-111">Set the active identity certificate for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="e9bb8-112">nx_secure_tls_client_psk_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-112">nx_secure_tls_client_psk_set</span></span>](#nx_secure_tls_client_psk_set)
  - <span data-ttu-id="e9bb8-113">Ustawianie klucza Pre_Shared sesji klienta bezpiecznego TLS NetX</span><span class="sxs-lookup"><span data-stu-id="e9bb8-113">Set a Pre_Shared Key for a NetX Secure TLS Client Session</span></span>
- [<span data-ttu-id="e9bb8-114">nx_secure_tls_initialize</span><span class="sxs-lookup"><span data-stu-id="e9bb8-114">nx_secure_tls_initialize</span></span>](#nx_secure_tls_initialize)
  - <span data-ttu-id="e9bb8-115">Inicjuje moduł NetX Secure TLS]</span><span class="sxs-lookup"><span data-stu-id="e9bb8-115">Initializes the NetX Secure TLS module]</span></span>
- [<span data-ttu-id="e9bb8-116">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="e9bb8-116">nx_secure_tls_local_certificate_add</span></span>](#nx_secure_tls_local_certificate_add)
  - <span data-ttu-id="e9bb8-117">Dodawanie certyfikatu lokalnego do bezpiecznej sesji TLS netx</span><span class="sxs-lookup"><span data-stu-id="e9bb8-117">Add a local certificate to NetX Secure TLS Session</span></span>
- [<span data-ttu-id="e9bb8-118">nx_secure_tls_local_certificate_find</span><span class="sxs-lookup"><span data-stu-id="e9bb8-118">nx_secure_tls_local_certificate_find</span></span>](#nx_secure_tls_local_certificate_find)
  - <span data-ttu-id="e9bb8-119">Znajdowanie certyfikatu lokalnego w bezpiecznej sesji TLS netx według nazwy pospolitej</span><span class="sxs-lookup"><span data-stu-id="e9bb8-119">Find a local certificate in a NetX Secure TLS Session by Common Name</span></span>
- [<span data-ttu-id="e9bb8-120">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="e9bb8-120">nx_secure_tls_local_certificate_remove</span></span>](#nx_secure_tls_local_certificate_remove)
  - <span data-ttu-id="e9bb8-121">Usuwanie certyfikatu lokalnego z bezpiecznej sesji TLS netx</span><span class="sxs-lookup"><span data-stu-id="e9bb8-121">Remove local certificate from NetX Secure TLS Session</span></span>
- [<span data-ttu-id="e9bb8-122">nx_secure_tls_metadata_size_calculate</span><span class="sxs-lookup"><span data-stu-id="e9bb8-122">nx_secure_tls_metadata_size_calculate</span></span>](#nx_secure_tls_metadata_size_calculate)
  - <span data-ttu-id="e9bb8-123">Obliczanie rozmiaru metadanych kryptograficznych dla bezpiecznej sesji TLS NetX</span><span class="sxs-lookup"><span data-stu-id="e9bb8-123">Calculate size of cryptographic metadata for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="e9bb8-124">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="e9bb8-124">nx_secure_tls_packet_allocate</span></span>](#nx_secure_tls_packet_allocate)
  - <span data-ttu-id="e9bb8-125">Przydzielanie pakietu dla sesji protokołu NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="e9bb8-125">Allocate a packet for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="e9bb8-126">nx_secure_tls_psk_add</span><span class="sxs-lookup"><span data-stu-id="e9bb8-126">nx_secure_tls_psk_add</span></span>](#nx_secure_tls_psk_add)
  - <span data-ttu-id="e9bb8-127">Dodawanie klucza Pre_Shared do bezpiecznej sesji TLS netx</span><span class="sxs-lookup"><span data-stu-id="e9bb8-127">Add a Pre_Shared Key to a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="e9bb8-128">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="e9bb8-128">nx_secure_tls_remote_certificate_allocate</span></span>](#nx_secure_tls_remote_certificate_allocate)
  - <span data-ttu-id="e9bb8-129">Przydzielanie miejsca dla certyfikatu dostarczonego przez zdalnego hosta TLS</span><span class="sxs-lookup"><span data-stu-id="e9bb8-129">Allocate space for the certificate provided by a remote TLS host</span></span>
- [<span data-ttu-id="e9bb8-130">nx_secure_tls_remote_certificate_buffer_allocate</span><span class="sxs-lookup"><span data-stu-id="e9bb8-130">nx_secure_tls_remote_certificate_buffer_allocate</span></span>](#nx_secure_tls_remote_certificate_buffer_allocate)
  - <span data-ttu-id="e9bb8-131">Przydzielanie miejsca dla wszystkich certyfikatów dostarczonych przez zdalnego hosta TLS</span><span class="sxs-lookup"><span data-stu-id="e9bb8-131">Allocate space for all certificates provided by a remote TLS host</span></span>
- [<span data-ttu-id="e9bb8-132">nx_secure_tls_remote_certificate_free_all</span><span class="sxs-lookup"><span data-stu-id="e9bb8-132">nx_secure_tls_remote_certificate_free_all</span></span>](#nx_secure_tls_remote_certificate_free_all)
  - <span data-ttu-id="e9bb8-133">Wolne miejsce przydzielone dla certyfikatów przychodzących</span><span class="sxs-lookup"><span data-stu-id="e9bb8-133">Free space allocated for incoming certificates</span></span>
- [<span data-ttu-id="e9bb8-134">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="e9bb8-134">nx_secure_tls_server_certificate_add</span></span>](#nx_secure_tls_server_certificate_add)
  - <span data-ttu-id="e9bb8-135">Dodawanie certyfikatu przeznaczonego specjalnie dla serwerów TLS przy użyciu identyfikatora liczbowego</span><span class="sxs-lookup"><span data-stu-id="e9bb8-135">Add a certificate specifically for TLS servers using a numeric identifier</span></span>
- [<span data-ttu-id="e9bb8-136">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="e9bb8-136">nx_secure_tls_server_certificate_find</span></span>](#nx_secure_tls_server_certificate_find)
  - <span data-ttu-id="e9bb8-137">Znajdowanie certyfikatu przy użyciu identyfikatora liczbowego</span><span class="sxs-lookup"><span data-stu-id="e9bb8-137">Find a certificate using a numeric identifier</span></span>
- [<span data-ttu-id="e9bb8-138">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="e9bb8-138">nx_secure_tls_server_certificate_remove</span></span>](#nx_secure_tls_server_certificate_remove)
  - <span data-ttu-id="e9bb8-139">Usuwanie certyfikatu serwera lokalnego przy użyciu identyfikatora liczbowego</span><span class="sxs-lookup"><span data-stu-id="e9bb8-139">Remove a local server certificate using a numeric identifier</span></span>
- [<span data-ttu-id="e9bb8-140">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-140">nx_secure_tls_session_certificate_callback_set</span></span>](#nx_secure_tls_session_certificate_callback_set)
  - <span data-ttu-id="e9bb8-141">Konfigurowanie wywołania zwrotnego dla usługi TLS na użytek dodatkowej weryfikacji certyfikatu</span><span class="sxs-lookup"><span data-stu-id="e9bb8-141">Set up a callback for TLS to use for additional certificate validation</span></span>
- [<span data-ttu-id="e9bb8-142">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-142">nx_secure_tls_session_client_callback_set</span></span>](#nx_secure_tls_session_client_callback_set)
  - <span data-ttu-id="e9bb8-143">Konfigurowanie wywołania zwrotnego dla usługi TLS do wywoływania na początku uściślinia klienta TLS</span><span class="sxs-lookup"><span data-stu-id="e9bb8-143">Set up a callback for TLS to invoke at the beginning of a TLS Client handshake</span></span>
- [<span data-ttu-id="e9bb8-144">nx_secure_tls_session_x509_client_verify_configure</span><span class="sxs-lookup"><span data-stu-id="e9bb8-144">nx_secure_tls_session_x509_client_verify_configure</span></span>](#nx_secure_tls_session_x509_client_verify_configure)
  - <span data-ttu-id="e9bb8-145">Włączanie weryfikacji X.509 klienta i przydzielanie miejsca dla certyfikatów klienta</span><span class="sxs-lookup"><span data-stu-id="e9bb8-145">Enable client X.509 verification and allocate space for client certificates</span></span>
- [<span data-ttu-id="e9bb8-146">nx_secure_tls_session_client_verify_disable</span><span class="sxs-lookup"><span data-stu-id="e9bb8-146">nx_secure_tls_session_client_verify_disable</span></span>](#nx_secure_tls_session_client_verify_disable)
  - <span data-ttu-id="e9bb8-147">Wyłączanie uwierzytelniania certyfikatu klienta dla bezpiecznej sesji protokołu TLS netx</span><span class="sxs-lookup"><span data-stu-id="e9bb8-147">Disable Client Certificate Authentication for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="e9bb8-148">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="e9bb8-148">nx_secure_tls_session_client_verify_enable</span></span>](#nx_secure_tls_session_client_verify_enable)
  - <span data-ttu-id="e9bb8-149">Włączanie uwierzytelniania certyfikatu klienta dla bezpiecznej sesji protokołu TLS netx</span><span class="sxs-lookup"><span data-stu-id="e9bb8-149">Enable Client Certificate Authentication for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="e9bb8-150">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="e9bb8-150">nx_secure_tls_session_create</span></span>](#nx_secure_tls_session_create)
  - <span data-ttu-id="e9bb8-151">Tworzenie bezpiecznej sesji TLS netx na celu bezpieczną komunikację</span><span class="sxs-lookup"><span data-stu-id="e9bb8-151">Create a NetX Secure TLS Session for secure communications</span></span>
- [<span data-ttu-id="e9bb8-152">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="e9bb8-152">nx_secure_tls_session_delete</span></span>](#nx_secure_tls_session_delete)
  - <span data-ttu-id="e9bb8-153">Usuwanie bezpiecznej sesji TLS netx</span><span class="sxs-lookup"><span data-stu-id="e9bb8-153">Delete a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="e9bb8-154">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="e9bb8-154">nx_secure_tls_session_end</span></span>](#nx_secure_tls_session_end)
  - <span data-ttu-id="e9bb8-155">Zakończenie aktywnej bezpiecznej sesji TLS netx</span><span class="sxs-lookup"><span data-stu-id="e9bb8-155">End an active NetX Secure TLS Session</span></span>
- [<span data-ttu-id="e9bb8-156">nx_secure_tls_session_packet_buffer_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-156">nx_secure_tls_session_packet_buffer_set</span></span>](#nx_secure_tls_session_packet_buffer_set)
  - <span data-ttu-id="e9bb8-157">Ustawianie buforu ponownego zestawu pakietów dla bezpiecznej sesji protokołu TLS NetX</span><span class="sxs-lookup"><span data-stu-id="e9bb8-157">Set the packet reassembly buffer for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="e9bb8-158">nx_secure_tls_session_protocol_version_override</span><span class="sxs-lookup"><span data-stu-id="e9bb8-158">nx_secure_tls_session_protocol_version_override</span></span>](#nx_secure_tls_session_protocol_version_override)
  - <span data-ttu-id="e9bb8-159">Zastąp domyślną wersję protokołu TLS dla bezpiecznej sesji TLS NetX</span><span class="sxs-lookup"><span data-stu-id="e9bb8-159">Override the default TLS protocol version for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="e9bb8-160">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="e9bb8-160">nx_secure_tls_session_receive</span></span>](#nx_secure_tls_session_receive)
  - <span data-ttu-id="e9bb8-161">Odbieranie danych z bezpiecznej sesji TLS netx</span><span class="sxs-lookup"><span data-stu-id="e9bb8-161">Receive data from a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="e9bb8-162">nx_secure_tls_session_renegotiate_callback_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-162">nx_secure_tls_session_renegotiate_callback_set</span></span>](#nx_secure_tls_session_renegotiate_callback_set)
  - <span data-ttu-id="e9bb8-163">Przypisywanie wywołania zwrotnego, które będzie wywoływane na początku ponownego negocjowania sesji</span><span class="sxs-lookup"><span data-stu-id="e9bb8-163">Assign a callback that will be invoked at the beginning of a session renegotiation</span></span>
- [<span data-ttu-id="e9bb8-164">nx_secure_tls_session_renegotiate</span><span class="sxs-lookup"><span data-stu-id="e9bb8-164">nx_secure_tls_session_renegotiate</span></span>](#nx_secure_tls_session_renegotiate)
  - <span data-ttu-id="e9bb8-165">Inicjowanie negocjacji ponownego negocjowania sesji z hostem zdalnym</span><span class="sxs-lookup"><span data-stu-id="e9bb8-165">Initiate a session renegotiation handshake with the remote host</span></span>
- [<span data-ttu-id="e9bb8-166">nx_secure_tls_session_reset</span><span class="sxs-lookup"><span data-stu-id="e9bb8-166">nx_secure_tls_session_reset</span></span>](#nx_secure_tls_session_reset)
  - <span data-ttu-id="e9bb8-167">Wyczyszczanie i resetowanie bezpiecznej sesji TLS netx</span><span class="sxs-lookup"><span data-stu-id="e9bb8-167">Clear out and reset a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="e9bb8-168">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="e9bb8-168">nx_secure_tls_session_send</span></span>](#nx_secure_tls_session_send)
  - <span data-ttu-id="e9bb8-169">Wysyłanie danych za pośrednictwem bezpiecznej sesji TLS netx</span><span class="sxs-lookup"><span data-stu-id="e9bb8-169">Send data through a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="e9bb8-170">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-170">nx_secure_tls_session_server_callback_set</span></span>](#nx_secure_tls_session_server_callback_set)
  - <span data-ttu-id="e9bb8-171">Konfigurowanie wywołania zwrotnego dla TLS do wywołania na początku uściślniania serwera TLS</span><span class="sxs-lookup"><span data-stu-id="e9bb8-171">Set up a callback for TLS to invoke at the beginning of a TLS Server handshake</span></span>
- [<span data-ttu-id="e9bb8-172">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="e9bb8-172">nx_secure_tls_session_sni_extension_parse</span></span>](#nx_secure_tls_session_sni_extension_parse)
  - <span data-ttu-id="e9bb8-173">Analizowanie rozszerzenia Oznaczanie nazwy serwera (SNI) otrzymanego od klienta TLS</span><span class="sxs-lookup"><span data-stu-id="e9bb8-173">Parse a Server Name Indication (SNI) extension received from a TLS Client</span></span>
- [<span data-ttu-id="e9bb8-174">nx_secure_tls_session_sni_extension_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-174">nx_secure_tls_session_sni_extension_set</span></span>](#nx_secure_tls_session_sni_extension_set)
  - <span data-ttu-id="e9bb8-175">Ustawianie nazwy DNS Oznaczanie nazwy serwera (SNI) do wysyłania do serwera zdalnego</span><span class="sxs-lookup"><span data-stu-id="e9bb8-175">Set a Server Name Indication (SNI) extension DNS name to send to a remote Server</span></span>
- [<span data-ttu-id="e9bb8-176">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="e9bb8-176">nx_secure_tls_session_start</span></span>](#nx_secure_tls_session_start)
  - <span data-ttu-id="e9bb8-177">Uruchamianie bezpiecznej sesji TLS netx</span><span class="sxs-lookup"><span data-stu-id="e9bb8-177">Start a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="e9bb8-178">nx_secure_tls_session_time_function_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-178">nx_secure_tls_session_time_function_set</span></span>](#nx_secure_tls_session_time_function_set)
  - <span data-ttu-id="e9bb8-179">Przypisywanie funkcji znacznika czasu do bezpiecznej sesji TLS netx</span><span class="sxs-lookup"><span data-stu-id="e9bb8-179">Assign a timestamp function to a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="e9bb8-180">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="e9bb8-180">nx_secure_tls_trusted_certificate_add</span></span>](#nx_secure_tls_trusted_certificate_add)
  - <span data-ttu-id="e9bb8-181">Dodawanie zaufanego certyfikatu do bezpiecznej sesji TLS netx</span><span class="sxs-lookup"><span data-stu-id="e9bb8-181">Add trusted certificate to NetX Secure TLS Session</span></span>
- [<span data-ttu-id="e9bb8-182">nx_secure_tls_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="e9bb8-182">nx_secure_tls_trusted_certificate_remove</span></span>](#nx_secure_tls_trusted_certificate_remove)
  - <span data-ttu-id="e9bb8-183">Usuwanie zaufanego certyfikatu z bezpiecznej sesji TLS netx</span><span class="sxs-lookup"><span data-stu-id="e9bb8-183">Remove trusted certificate from NetX Secure TLS Session</span></span>
- [<span data-ttu-id="e9bb8-184">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="e9bb8-184">nx_secure_x509_certificate_initialize</span></span>](#nx_secure_x509_certificate_initialize)
  - <span data-ttu-id="e9bb8-185">Inicjowanie certyfikatu X.509 dla bezpiecznego TLS NetX</span><span class="sxs-lookup"><span data-stu-id="e9bb8-185">Initialize X.509 Certificate for NetX Secure TLS</span></span>
- [<span data-ttu-id="e9bb8-186">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="e9bb8-186">nx_secure_x509_common_name_dns_check</span></span>](#nx_secure_x509_common_name_dns_check)
  - <span data-ttu-id="e9bb8-187">Sprawdzanie nazwy DNS względem certyfikatu X.509</span><span class="sxs-lookup"><span data-stu-id="e9bb8-187">Check DNS name against X.509 Certificate</span></span>
- [<span data-ttu-id="e9bb8-188">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="e9bb8-188">nx_secure_x509_crl_revocation_check</span></span>](#nx_secure_x509_crl_revocation_check)
  - <span data-ttu-id="e9bb8-189">Sprawdź certyfikat X.509 względem podanej listy odwołania certyfikatów (CRL)]</span><span class="sxs-lookup"><span data-stu-id="e9bb8-189">Check X.509 Certificate against a supplied Certificate Revocation List (CRL)]</span></span>
- [<span data-ttu-id="e9bb8-190">nx_secure_x509_dns_name_initialize</span><span class="sxs-lookup"><span data-stu-id="e9bb8-190">nx_secure_x509_dns_name_initialize</span></span>](#nx_secure_x509_dns_name_initialize)
  - <span data-ttu-id="e9bb8-191">Inicjowanie struktury nazw DNS X.509</span><span class="sxs-lookup"><span data-stu-id="e9bb8-191">Initialize an X.509 DNS name structure</span></span>
- [<span data-ttu-id="e9bb8-192">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="e9bb8-192">nx_secure_x509_extended_key_usage_extension_parse</span></span>](#nx_secure_x509_extended_key_usage_extension_parse)
  - <span data-ttu-id="e9bb8-193">Znajdowanie i analizowanie rozszerzenia rozszerzonego użycia klucza X.509 w certyfikacie X.509</span><span class="sxs-lookup"><span data-stu-id="e9bb8-193">Find and parse an X.509 extended key usage extension in an X.509 certificate</span></span>
- [<span data-ttu-id="e9bb8-194">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="e9bb8-194">nx_secure_x509_extension_find</span></span>](#nx_secure_x509_extension_find)
  - <span data-ttu-id="e9bb8-195">Znajdowanie i zwracanie rozszerzenia X.509 w certyfikacie X.509</span><span class="sxs-lookup"><span data-stu-id="e9bb8-195">Find and return an X.509 extension in an X.509 certificate</span></span>
- [<span data-ttu-id="e9bb8-196">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="e9bb8-196">nx_secure_x509_key_usage_extension_parse</span></span>](#nx_secure_x509_key_usage_extension_parse)
  - <span data-ttu-id="e9bb8-197">Znajdowanie i analizowanie rozszerzenia X.509 użycia klucza w certyfikacie X.509</span><span class="sxs-lookup"><span data-stu-id="e9bb8-197">Find and parse an X.509 Key Usage extension in an X.509 certificate</span></span>

## <a name="nx_secure_crypto_table_self_test"></a><span data-ttu-id="e9bb8-198">nx_secure_crypto_table_self_test</span><span class="sxs-lookup"><span data-stu-id="e9bb8-198">nx_secure_crypto_table_self_test</span></span>

<span data-ttu-id="e9bb8-199">Wykonywanie samodzielnego testowania metod kryptograficznych</span><span class="sxs-lookup"><span data-stu-id="e9bb8-199">Perform self-test on the crypto methods</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-200">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-200">Prototype</span></span>

```C
UINT nx_secure_crypto_table_self_test(
                                  const NX_SECURE_TLS_CRYPTO *crypto_table,
                                  VOID *metadata, UINT metadata_size);
```

### <a name="description"></a><span data-ttu-id="e9bb8-201">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-201">Description</span></span>

<span data-ttu-id="e9bb8-202">Ta usługa jest uruchamiana za pośrednictwem metody kryptograficznego samokontroli w celu zweryfikowania.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-202">This service runs through the crypto method self tests to validate.</span></span> <span data-ttu-id="e9bb8-203">Samodzielny test jest dostępny tylko wtedy, gdy biblioteka NetX Secure została s zbudowana z NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK biblioteki.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-203">The self test is available only if NetX Secure library is built with the symbol NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK defined.</span></span>

<span data-ttu-id="e9bb8-204">Dla każdej obsługiwanej metody kryptograficzne autotest udostępnia wstępnie zdefiniowane dane wejściowe i sprawdza, czy dane wyjściowe są zgodnie ze wstępnie zdefiniowaną oczekiwaną wartością.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-204">For each supported crypto method, the self test provides pre-defined input data, and verified the output matches the pre-defined expected value.</span></span>

<span data-ttu-id="e9bb8-205">Samodzielny test kryptograficzny netX Secure obsługuje następujące algorytmy i rozmiary kluczy:</span><span class="sxs-lookup"><span data-stu-id="e9bb8-205">NetX Secure crypto self test supports the following algorithms and key sizes:</span></span>

- <span data-ttu-id="e9bb8-206">DES: szyfrowanie i odszyfrowywanie</span><span class="sxs-lookup"><span data-stu-id="e9bb8-206">DES: encryption and decryption</span></span>
- <span data-ttu-id="e9bb8-207">Triple DES (3DES): szyfrowanie i odszyfrowywanie</span><span class="sxs-lookup"><span data-stu-id="e9bb8-207">Triple DES (3DES): encryption and decryption</span></span>
- <span data-ttu-id="e9bb8-208">AES: 128-, 192-, 256-bitowy rozmiar klucza, szyfrowanie i odszyfrowywanie, w trybie CBC i trybie licznika.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-208">AES: 128-, 192-, 256-bit key size, encryption and decryption, in CBC mode and counter mode.</span></span>
- <span data-ttu-id="e9bb8-209">HMAC-MD5: uwierzytelnianie i obliczanie skrótów</span><span class="sxs-lookup"><span data-stu-id="e9bb8-209">HMAC-MD5: authentication and hash computation</span></span>
- <span data-ttu-id="e9bb8-210">HMAC-SHA: SHA1-96, SHA1-160, SHA2-256, SHA2-384, SHA2-512, uwierzytelnianie i obliczanie skrótów</span><span class="sxs-lookup"><span data-stu-id="e9bb8-210">HMAC-SHA: SHA1-96, SHA1-160, SHA2-256, SHA2-384, SHA2- 512, authentication and hash computation</span></span>
- <span data-ttu-id="e9bb8-211">MD5: uwierzytelnianie</span><span class="sxs-lookup"><span data-stu-id="e9bb8-211">MD5: authentication</span></span>
- <span data-ttu-id="e9bb8-212">Funkcja pseudolosowa (PRF): PRF_HMAC_SHA1 i PRF_HMAC_SHA2-256</span><span class="sxs-lookup"><span data-stu-id="e9bb8-212">Pseudo-random Function (PRF): PRF_HMAC_SHA1 and PRF_HMAC_SHA2-256</span></span>
- <span data-ttu-id="e9bb8-213">RSA: 1024-, 2048-, 4096-bitowa operacja modulo mocy RSA</span><span class="sxs-lookup"><span data-stu-id="e9bb8-213">RSA: 1024-, 2048-, 4096-bit RSA power-modulus operation</span></span>
- <span data-ttu-id="e9bb8-214">SHA: uwierzytelnianie SHA1 (96- i 160-bitowe), SHA2 (256-bitowe, 384-bitowe, 512-bitowe)</span><span class="sxs-lookup"><span data-stu-id="e9bb8-214">SHA: SHA1 (96- and 160-bit), SHA2 (256bit, 384bit, 512bit) authentication</span></span>

<span data-ttu-id="e9bb8-215">Ta funkcja ma wbudowane wektory dla wymienionych powyżej algorytmów kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-215">This function has the built-in vectors for the crypto algorithms listed above.</span></span> <span data-ttu-id="e9bb8-216">Testuje jednak tylko te, które zostały wymienione *w cipher_table* przekazane do tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-216">However it only tests the ones listed in the *cipher_table* passed into this function.</span></span> <span data-ttu-id="e9bb8-217">Na przykład w przypadku sesji TLS używany jest tylko szyfrsuite TLS_RSA_WITH_AES_128_CBC_SHA, ta funkcja wykona własny test na RSA (1024-, 2048-, 4096-bitowych), AES-CBC (128-bitowych) i SHA1.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-217">For example, for a TLS session uses only the ciphersuite TLS_RSA_WITH_AES_128_CBC_SHA, this function will perform self test on the RSA (1024-, 2048-, 4096-bit), AES-CBC (128-bit) and SHA1.</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-218">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-218">Parameters</span></span>

- <span data-ttu-id="e9bb8-219">**crypto_table** Wskaźnik do tabeli kryptograficznych używanej przez sesję TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-219">**crypto_table** Pointer to the crypto table being used by the TLS session.</span></span> <span data-ttu-id="e9bb8-220">Jest to ta sama crypto_table przekazywana do **_wywołania nx_secure_tls_session_create()._**</span><span class="sxs-lookup"><span data-stu-id="e9bb8-220">This is the same crypto_table being passed into the **_nx_secure_tls_session_create()_** call.</span></span>
- <span data-ttu-id="e9bb8-221">**metadane** Wskaźnik do miejsca dla obszaru metadanych kryptografii.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-221">**metadata** Pointer to space for cryptography metadata area.</span></span> <span data-ttu-id="e9bb8-222">.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-222">.</span></span>
- <span data-ttu-id="e9bb8-223">**metadata_size** Rozmiar buforu metadanych.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-223">**metadata_size** Size of the metadata buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-224">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-224">Return Values</span></span>

- <span data-ttu-id="e9bb8-225">**NX_SECURE_TLS_SUCCESS** (0x00) Pomyślnie przetestowano podane metody kryptograficzne.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-225">**NX_SECURE_TLS_SUCCESS** (0x00) Successfully tested the crypto methods provided.</span></span>
- <span data-ttu-id="e9bb8-226">**NX_PTR_ERROR** (0x07) Nieprawidłowa struktura metody kryptograficznych</span><span class="sxs-lookup"><span data-stu-id="e9bb8-226">**NX_PTR_ERROR** (0x07) Invalid crypto method structure</span></span>
- <span data-ttu-id="e9bb8-227">**NX_NOT_SUCCESSFUL** (0x43) Crypto self test fails (Samodzielne testowanie kryptograficzne kończy się niepowodzeniem).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-227">**NX_NOT_SUCCESSFUL** (0x43) Crypto self test fails.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-228">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-228">Allowed From</span></span>

<span data-ttu-id="e9bb8-229">Inicjowanie, wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-229">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-230">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-230">Example</span></span>

```C
/* crypto_tls_ciphers is the cipher table for the TLS session. */
/* metadata_buffer is the memory area used by the cipher functions. */

/* The following function verifies the supplied ciphersuties using the built-in
   self test. */

if (nx_secure_crypto_table_self_test(&crypto_tls_ciphers, metadata_buffer,
    sizeof(metadata_buffer)))
{
    printf("Crypto self test failed!\r\n");
    exit(0);
}
else
{
    printf("Crypto self test succeed!\r\n");
}

/* Now the ciphersuites are successfully test, it can be used in
   nx_secure_tls_session_create() */
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-231">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-231">See Also</span></span>

- <span data-ttu-id="e9bb8-232">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="e9bb8-232">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_module_hash_compute"></a><span data-ttu-id="e9bb8-233">nx_secure_module_hash_compute</span><span class="sxs-lookup"><span data-stu-id="e9bb8-233">nx_secure_module_hash_compute</span></span>

<span data-ttu-id="e9bb8-234">Oblicza wartość skrótu przy użyciu funkcji skrótu dostarczonej przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="e9bb8-234">Computes hash value using user-supplied hash function</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-235">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-235">Prototype</span></span>

```C
UINT nx_secure_module_hash_compute(
                      NX_CRYPTO_METHOD *hamc_ptr,
                      UINT start_address, UINT end_address,
                      UCHAR *key, UINT key_length,
                      VOID *metadata, UINT metadata_size,
                      UCHAR *output_buffer, UINT output_buffer_size,
                      UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="e9bb8-236">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-236">Description</span></span>

<span data-ttu-id="e9bb8-237">Ta funkcja oblicza wartość skrótu strumienia danych w określonym obszarze pamięci przy użyciu podanej metody kryptograficznej HMAC i ciągu klucza.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-237">This function computes the hash value of the data stream in the specified memory area, using supplied HMAC crypto method and the key string.</span></span> <span data-ttu-id="e9bb8-238">Funkcja obliczeniowa skrótu modułu jest dostępna tylko wtedy, gdy biblioteka NetX Secure jest budowaną przy użyciu następującego symbolu: NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK</span><span class="sxs-lookup"><span data-stu-id="e9bb8-238">The module hash compute function is available only if NetX Secure library is built with the following symbol being defined: NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-239">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-239">Parameters</span></span>

- <span data-ttu-id="e9bb8-240">**hmac_ptr** Wskaźnik do metody kryptograficznej HMAC używanej do obliczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-240">**hmac_ptr** Pointer to the HMAC crypto method being used for the hash value computation.</span></span>
- <span data-ttu-id="e9bb8-241">**start_address** Adres początkowy buforu danych</span><span class="sxs-lookup"><span data-stu-id="e9bb8-241">**start_address** The starting address of the data buffer</span></span>
- <span data-ttu-id="e9bb8-242">**end_address** Końcowy adres buforu danych.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-242">**end_address** The ending address of the data buffer.</span></span> <span data-ttu-id="e9bb8-243">Należy pamiętać, że obliczenia wartości skrótu nie obejmują danych w tym end_address.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-243">Note that hash computation does not cover the data at this end_address.</span></span>
- <span data-ttu-id="e9bb8-244">**klucz** Ciąg klucza używany w obliczeniach HMAC.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-244">**key** The key string being used in the HMAC computation.</span></span>
- <span data-ttu-id="e9bb8-245">**key_length** Rozmiar ciągu klucza w bajtach</span><span class="sxs-lookup"><span data-stu-id="e9bb8-245">**key_length** The size of the key string, in bytes</span></span>
- <span data-ttu-id="e9bb8-246">**metadane** Wskaźnik do miejsca używanego przez algorytm HMAC.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-246">**metadata** Pointer to space used by the HMAC algorithm.</span></span>
- <span data-ttu-id="e9bb8-247">**metadata_size** Rozmiar buforu metadanych.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-247">**metadata_size** Size of the metadata buffer.</span></span>
- <span data-ttu-id="e9bb8-248">**output_buffer** Lokalizacja pamięci, w której są przechowywane dane wyjściowe skrótu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-248">**output_buffer** The memory location where the hash output is being stored at.</span></span>
- <span data-ttu-id="e9bb8-249">**output_buffer_size** Dostępne miejsce buforu wyjściowego w bajtach</span><span class="sxs-lookup"><span data-stu-id="e9bb8-249">**output_buffer_size** The available space of the output buffer, in bytes</span></span>
- <span data-ttu-id="e9bb8-250">**actual_size** Zwracana przez funkcję wskazująca rzeczywistą liczbę bajtów zapisywanych w output_buffer.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-250">**actual_size** Returned by the function indicating the actual number of bytes being written into the output_buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-251">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-251">Return Values</span></span>

- <span data-ttu-id="e9bb8-252">**0** Pomyślnie obliczono wartość skrótu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-252">**0** Successfully computed the hash value.</span></span>
- <span data-ttu-id="e9bb8-253">**1 Obliczanie** skrótu nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-253">**1** The hash computation failed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-254">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-254">Allowed From</span></span>

<span data-ttu-id="e9bb8-255">Inicjowanie, wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-255">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-256">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-256">Example</span></span>

```C
/* Define the HMAC SHA256 method */
NX_CRYPTO_METHOD hmac_sha256 =
{
    NX_CRYPTO_AUTHENTICATION_HMAC_SHA2_256,    /* HMAC SHA256 algorithm  */
    0,                                         /* Key size, not used     */
    0,                                         /* IV size, not used      */
    NX_CRYPTO_HMAC_SHA256_ICV_FULL_LEN_IN_BITS,/* Transmitted ICV size   */
    NX_CRYPTO_SHA2_BLOCK_SIZE_IN_BYTES,        /* Block size in bytes    */
    sizeof(NX_CRYPTO_SHA256_HMAC),             /* Metadata size in bytes */
    _nx_crypto_method_hmac_sha256_init,        /* HMAC SHA256 init       */
    _nx_crypto_method_hmac_sha256_cleanup,     /* HMAC SHA256 cleanup    */
    _nx_crypto_method_hmac_sha256_operation    /* HMAC SHA256 operation  */
};

/* Define the hash key being used. */
const CHAR hash_key = “my hash key”;

/* Define starting address. */
UINT starting_address = 0x10000;

/* Define the ending address.
   Note that the hash computation covers the memory location
   before the ending address. */
UINT ending_address = 0x11000;

/* Declare the output buffer. */
#define OUTPUT_BUFFER_SIZE
UCHAR output_buffer[OUTPUT_BUFFER_SIZE];

UINT actual_size;

/* Declare 1K bytes of metadata buffer area. */
UCHAR metadata_buffer[1024];

/* Compute the hash value of the data between 0x10000 – 0x10FFF */
nx_secure_module_hash_compute(&hmac_sha256,
                              starting_address, ending_address,
                              hash_key, strlen(hash_key),
                              metadata_buffer, sizeof(metadata_buffer),
                              output_buffer, OUTPUT_BUFFER_SIZE, &actual_size);

/* If this function returns “0”, the hash value has been computed and is stored
   in output_buffer. */
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-257">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-257">See Also</span></span>

- <span data-ttu-id="e9bb8-258">nx_secure_crypto_method_self_test</span><span class="sxs-lookup"><span data-stu-id="e9bb8-258">nx_secure_crypto_method_self_test</span></span>

## <a name="nx_secure_tls_active_certificate_set"></a><span data-ttu-id="e9bb8-259">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-259">nx_secure_tls_active_certificate_set</span></span>

<span data-ttu-id="e9bb8-260">Ustawianie aktywnego certyfikatu tożsamości dla bezpiecznej sesji TLS netx</span><span class="sxs-lookup"><span data-stu-id="e9bb8-260">Set the active identity certificate for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-261">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-261">Prototype</span></span>

```C
UINT  nx_secure_tls_active_certificate_set(
                   NX_SECURE_TLS_SESSION *tls_session,
                   NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a><span data-ttu-id="e9bb8-262">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-262">Description</span></span>

<span data-ttu-id="e9bb8-263">Ta usługa jest przeznaczona do wywoływania z poziomu wywołania zwrotnego sesji (zobacz nx_secure_tls_session_client_callback_set i nx_secure_tls_session_server_callback_set).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-263">This service is intended to be called from within a session callback (see nx_secure_tls_session_client_callback_set and nx_secure_tls_session_server_callback_set).</span></span> <span data-ttu-id="e9bb8-264">W przypadku wywoływania z wcześniej zainicjowaną NX_SECURE_X509_CERT, ten certyfikat będzie używany zamiast domyślnego certyfikatu tożsamości.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-264">When called with a previously-initialized NX_SECURE_X509_CERT structure, that certificate will be used instead of the default identity certificate.</span></span> <span data-ttu-id="e9bb8-265">W większości przypadków certyfikat musi zostać dodany do magazynu lokalnego (zobacz nx_secure_tls_local_certificate_add) lub uściślić TLS może się nie powieść.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-265">In most cases, the certificate must have been added to the local store (see nx_secure_tls_local_certificate_add) or the TLS handshake may fail.</span></span>

<span data-ttu-id="e9bb8-266">Ta usługa jest przeznaczona do zezwalania na obsługę wielu certyfikatów tożsamości przez usługę TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-266">This service is intended to allow TLS to support multiple identity certificates.</span></span> <span data-ttu-id="e9bb8-267">Jest to przydatne w przypadku serwera TLS, który zapewnia wiele adresów sieciowych, dzięki czemu serwer może wybrać odpowiedni certyfikat do zapewnienia klientowi zdalnej w zależności od punktu wejścia klienta.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-267">This is useful for a TLS server that services multiple network addresses so the server can pick an appropriate certificate to provide to the remote client depending on the client's entrypoint.</span></span> <span data-ttu-id="e9bb8-268">W przypadku klienta TLS ta procedura może służyć do zmiany certyfikatu wysyłanego do serwera zdalnego w czasie wykonywania po tym, jak serwer zidentyfikował się w uściśleniu TLS (jest to bardziej rzadkie niż przypadek użycia serwera TLS).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-268">For a TLS client, this routine may be used to change the certificate sent to a remote server at runtime after the server has identified itself in the TLS handshake (this is more rare than the TLS server use-case).</span></span>

<span data-ttu-id="e9bb8-269">W przypadku, gdy wiele certyfikatów może mieć tę samą nazwę wyróżniającą X.509, należy dodać certyfikaty przy użyciu programu nx_secure_tls_server_certificate_add, co wprowadza identyfikator liczbowy oddzielony od certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-269">In the case where multiple certificates may share the same X.509 distinguished name, certificates will need to be added using nx_secure_tls_server_certificate_add, which introduces a numeric identifier separate from the certificate.</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-270">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-270">Parameters</span></span>

- <span data-ttu-id="e9bb8-271">**session_ptr** Wskaźnik do wystąpienia sesji TLS przekazany do wywołania zwrotnego sesji.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-271">**session_ptr** Pointer to a TLS Session instance passed into the session callback.</span></span>
- <span data-ttu-id="e9bb8-272">**certyfikat** Wskaźnik do zainicjowany certyfikat X.509, który ma być używany w bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-272">**certificate** Pointer to an initialized X.509 certificate that is to be used for the current session.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-273">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-273">Return Values</span></span>

- <span data-ttu-id="e9bb8-274">**NX_SUCCESS** (0x00) Pomyślne przypisanie certyfikatu do sesji.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-274">**NX_SUCCESS** (0x00) Successful assignment of certificate to session.</span></span>
- <span data-ttu-id="e9bb8-275">**NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji lub certyfikatu TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-275">**NX_PTR_ERROR** (0x07) Invalid TLS session or certificate pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-276">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-276">Allowed From</span></span>

<span data-ttu-id="e9bb8-277">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-277">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-278">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-278">Example</span></span>

```C
#define TLS_SNI_SERVER_NAME “www.example.com”
#define TLS_DEFAULT_SERVER_CERT_ID 2
#define TLS_EXAMPLE_CERT_ID 3


/* Callback for ClientHello extensions processing. */
static ULONG tls_server_callback(NX_SECURE_TLS_SESSION *tls_session,
                                 NX_SECURE_TLS_HELLO_EXTENSION *extensions,
                                 UINT num_extensions)
{
NX_SECURE_X509_DNS_NAME dns_name;
INT compare_value;
UINT status;
NX_SECURE_X509_CERT *cert_ptr;

    /* Grab a pointer to our default certificate in case the SNI extension is not
       available or the specified server name is unknown. */
    nx_secure_tls_server_certificate_find(tls_session, &cert_ptr,
                                     TLS_DEFAULT_SERVER_CERT_ID);


    /* Process Server Name Indication extension. */
    status = _nx_secure_tls_session_sni_extension_parse(tls_session, extensions,
                                                    num_extensions, &dns_name);

    /* If no extension found, that is OK. Use default certificate. */
    if(status == NX_SUCCESS)
    {
          /* SNI extension found, select an active certificate based on the server
             name. */

          /* Make sure our SNI name matches. */
          compare_value = memcmp(dns_name.nx_secure_x509_dns_name,
                                TLS_SNI_SERVER_NAME, strlen(TLS_SNI_SERVER_NAME));

          if(compare_value == 0 && dns_name.nx_secure_x509_dns_name_length !=
             strlen(TLS_SNI_SERVER_NAME))
          {
             /* Found a match, find the certificate we want to use. */
             _nx_secure_tls_server_certificate_find(tls_session, &cert_ptr,
                                                      TLS_EXAMPLE_CERT_ID);
          }
          else
          {
             /* No matching server name found. The application may choose to simply
                provide the default certificate (and probably resulting in an error
                in the remote client) or returning an error here to end the
                handshake. A user-defined non-zero error code will be sufficient –
                the error code will abort the TLS handshake and be returned to the
                caller that started the server. */
                return(0x500);
          }
      }
      else
      {
      }
      /* Set the certificate we want to use. */
      nx_secure_tls_active_certificate_set(tls_session, cert_ptr);

      /* Return success to continue TLS handshake. */
      return(NX_SUCCESS);
}

/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_TLS_SESSION server_tls_session;

/* Application where TLS session is started. */
void main()
{
    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_tls_session_create(&server_tls_session,
                                           &nx_crypto_tls_ciphers,
                                           server_crypto_metadata,
                                           sizeof(server_crypto_metadata));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_tls_session_create: 0x%x\n", status);
    }

    /* Setup our packet reassembly buffer. See
       nx_secure_tls_session_packet_buffer_set for more information. */
    nx_secure_tls_session_packet_buffer_set(&server_tls_session,
                                      server_packet_buffer,
                                      sizeof(server_packet_buffer));


    /* Set callback for server TLS extension handling. */
    _nx_secure_tls_session_server_callback_set(&server_tls_session,
                                              tls_server_callback);

    /* Initialize our certificates – certificate data defined elsewhere. See
       section “Importing X.509 Certificates into NetX Secure” for more
       information. */
    nx_secure_x509_certificate_initialize(&default_certificate,
                                      default_cert_der,
                                      default _cert_der_len, NX_NULL, 0,
                                      default_cert_key_der,
                                      default_cert_key_der_len,
                                      NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_tls_server_certificate_add(&server_tls_session,
                                         &default_certificate,
                                         TLS_DEFAULT_SERVER_CERT_ID);

    /* Alternative identity certificate, needs to have a private key! */
    nx_secure_x509_certificate_initialize(&example_certificate,
                                      example_cert_der,
                                      example cert_der_len, NX_NULL, 0,
                                      example_cert_key_der,
                                      example_cert_key_der_len,
                                      NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_tls_server_certificate_add(&server_tls_session,
                                         &example_certificate,
                                         TLS_EXAMPLE_CERT_ID);

    /* Now we can start the TLS session as normal. */
       …
}
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-279">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-279">See Also</span></span>

- <span data-ttu-id="e9bb8-280">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="e9bb8-280">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="e9bb8-281">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="e9bb8-281">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="e9bb8-282">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-282">nx_secure_tls_session_client_callback_set</span></span>
- <span data-ttu-id="e9bb8-283">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-283">nx_secure_tls_session_server_callback_set</span></span>
- <span data-ttu-id="e9bb8-284">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="e9bb8-284">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="e9bb8-285">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="e9bb8-285">nx_secure_tls_server_certificate_find</span></span>
- <span data-ttu-id="e9bb8-286">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="e9bb8-286">nx_secure_tls_server_certificate_remove</span></span>

## <a name="nx_secure_tls_client_psk_set"></a><span data-ttu-id="e9bb8-287">nx_secure_tls_client_psk_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-287">nx_secure_tls_client_psk_set</span></span>

<span data-ttu-id="e9bb8-288">Ustawianie klucza wstępnego dla bezpiecznej sesji klienta TLS NetX</span><span class="sxs-lookup"><span data-stu-id="e9bb8-288">Set a Pre-Shared Key for a NetX Secure TLS Client Session</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-289">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-289">Prototype</span></span>

```C
UINT  nx_secure_tls_client_psk_set(NX_SECURE_TLS_SESSION *session_ptr,
                              UCHAR *pre_shared_key, UINT psk_length,
                              UCHAR *psk_identity, UINT identity_length,
                              UCHAR *hint, UINT hint_length);
```

### <a name="description"></a><span data-ttu-id="e9bb8-290">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-290">Description</span></span>

<span data-ttu-id="e9bb8-291">Ta usługa dodaje klucz wstępny, jego ciąg tożsamości i wskazówkę tożsamości do bloku kontroli sesji TLS oraz ustawia klucz wstępny do późniejszego połączenia klienta TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-291">This service adds a Pre-Shared Key (PSK), its identity string, and an identity hint to a TLS Session control block, and sets that PSK to be used in subsequent TLS Client connections.</span></span> <span data-ttu-id="e9bb8-292">Jeśli są włączone i używane szyfry PSK, używany jest certyfikat cyfrowy, a nie certyfikat cyfrowy.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-292">The PSK is used in place of a digital certificate when PSK ciphersuites are enabled and used.</span></span>

<span data-ttu-id="e9bb8-293">W takim przypadku k OKI jest skojarzony z określonym zdalnym serwerem TLS, z którym klient TLS chce się komunikować.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-293">In this case, the PSK is associated with a specific remote TLS Server with which the TLS Client wishes to communicate.</span></span> <span data-ttu-id="e9bb8-294">Klucz psk ustawiony za pośrednictwem tego interfejsu API zostanie przekazany do zdalnego hosta serwera TLS podczas następnego ugody TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-294">The PSK set through this API will be provided to the remote TLS Server host during the next TLS handshake.</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-295">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-295">Parameters</span></span>

- <span data-ttu-id="e9bb8-296">**session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-296">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="e9bb8-297">**pre_shared_key** Rzeczywista wartość PSK.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-297">**pre_shared_key** The actual PSK value.</span></span>
- <span data-ttu-id="e9bb8-298">**psk_length** Długość wartości PSK.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-298">**psk_length** The length of the PSK value.</span></span>
- <span data-ttu-id="e9bb8-299">**psk_identity** Ciąg używany do identyfikowania tej wartości PSK.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-299">**psk_identity** A string used to identify this PSK value.</span></span>
- <span data-ttu-id="e9bb8-300">**identity_length** Długość tożsamości psk.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-300">**identity_length** The length of the PSK identity.</span></span>
- <span data-ttu-id="e9bb8-301">**wskazówka** Ciąg używany do wskazywania grupy psk do wyboru na serwerze TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-301">**hint** A string used to indicate which group of PSKs to choose from on a TLS server.</span></span>
- <span data-ttu-id="e9bb8-302">**hint_length** Długość ciągu wskazówki.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-302">**hint_length** The length of the hint string.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-303">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-303">Return Values</span></span>

- <span data-ttu-id="e9bb8-304">**NX_SUCCESS** (0x00) Pomyślne dodanie psk.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-304">**NX_SUCCESS** (0x00) Successful addition of PSK.</span></span>
- <span data-ttu-id="e9bb8-305">**NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-305">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="e9bb8-306">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Nie można dodać kolejnego psk.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-306">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Cannot add another PSK.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-307">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-307">Allowed From</span></span>

<span data-ttu-id="e9bb8-308">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-308">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-309">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-309">Example</span></span>

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to TLS session.  */
status =  nx_secure_tls_client_psk_set(&tls_session, psk, sizeof(psk), “psk_1”, 4,
“Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-310">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-310">See Also</span></span>

- <span data-ttu-id="e9bb8-311">nx_secure_tls_psk_add</span><span class="sxs-lookup"><span data-stu-id="e9bb8-311">nx_secure_tls_psk_add</span></span>
- <span data-ttu-id="e9bb8-312">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="e9bb8-312">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="e9bb8-313">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="e9bb8-313">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="e9bb8-314">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="e9bb8-314">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="e9bb8-315">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="e9bb8-315">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_initialize"></a><span data-ttu-id="e9bb8-316">nx_secure_tls_initialize</span><span class="sxs-lookup"><span data-stu-id="e9bb8-316">nx_secure_tls_initialize</span></span>

<span data-ttu-id="e9bb8-317">Inicjuje moduł NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="e9bb8-317">Initializes the NetX Secure TLS module</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-318">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-318">Prototype</span></span>

```C
VOID nx_secure_tls_initialize(VOID);
```

### <a name="description"></a><span data-ttu-id="e9bb8-319">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-319">Description</span></span>

<span data-ttu-id="e9bb8-320">Ta usługa inicjuje moduł NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-320">This service initializes the NetX Secure TLS module.</span></span> <span data-ttu-id="e9bb8-321">Musi zostać wywołana, aby można było uzyskać dostęp do innych usług NetX Secure.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-321">It must be called before other NetX Secure services can be accessed.</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-322">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-322">Parameters</span></span>

<span data-ttu-id="e9bb8-323">Brak</span><span class="sxs-lookup"><span data-stu-id="e9bb8-323">None</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-324">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-324">Return Values</span></span>

<span data-ttu-id="e9bb8-325">Brak</span><span class="sxs-lookup"><span data-stu-id="e9bb8-325">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-326">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-326">Allowed From</span></span>

<span data-ttu-id="e9bb8-327">Inicjowanie, wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-327">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-328">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-328">Example</span></span>

```C
/* Initializes the TLS module. */
Nx_secure_tls_initialize();
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-329">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-329">See Also</span></span>

- <span data-ttu-id="e9bb8-330">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="e9bb8-330">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_local_certificate_add"></a><span data-ttu-id="e9bb8-331">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="e9bb8-331">nx_secure_tls_local_certificate_add</span></span>

<span data-ttu-id="e9bb8-332">Dodawanie certyfikatu lokalnego do bezpiecznej sesji TLS netx</span><span class="sxs-lookup"><span data-stu-id="e9bb8-332">Add a local certificate to NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-333">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-333">Prototype</span></span>

```C
UINT  nx_secure_tls_local_certificate_add(
              NX_SECURE_TLS_SESSION *session_ptr,
              NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a><span data-ttu-id="e9bb8-334">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-334">Description</span></span>

<span data-ttu-id="e9bb8-335">Ta usługa dodaje zainicjowane NX_SECURE_X509_CERT struktury do magazynu lokalnego sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-335">This service adds an initialized NX_SECURE_X509_CERT structure instance to the local store of a TLS session.</span></span> <span data-ttu-id="e9bb8-336">Ten certyfikat może być używany przez stos TLS do identyfikowania urządzenia podczas procesu ugody TLS (jeśli został oznaczony jako certyfikat tożsamości podczas inicjowania struktury certyfikatów przy użyciu programu nx_secure_x509_certificate_initialize) lub jako wystawca w ramach łańcucha certyfikatów dostarczonego do hosta zdalnego podczas procesu ugody TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-336">This certificate may used by the TLS stack to identify the device during the TLS handshake (if it was marked as an identity certificate during initialization of the certificate structure using nx_secure_x509_certificate_initialize), or as an issuer as part of a certificate chain provided to the remote host during the TLS handshake.</span></span>

<span data-ttu-id="e9bb8-337">Jeśli wymaganych jest wiele certyfikatów lokalnych o tej samej nazwie pospolitej, można dodać certyfikaty przy użyciu *usługi nx_secure_tls_server_certificate_add* (zobacz ostrzeżenie poniżej).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-337">If multiple local certificates with the same Common Name are needed, certificates may be added using the *nx_secure_tls_server_certificate_add* service (see warning below).</span></span>

<span data-ttu-id="e9bb8-338">Certyfikat jest wymagany **w trybie** serwera TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-338">A certificate is **required** for TLS Server mode.</span></span>

<span data-ttu-id="e9bb8-339">Certyfikat jest opcjonalny *dla* trybu klienta TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-339">A certificate is *optional* for TLS Client mode.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e9bb8-340">*Tego interfejsu API nie należy używać z tą samą sesją TLS podczas korzystania z nx_secure_tls_server_certificate_add. Interfejs API certyfikatu serwera używa unikatowego identyfikatora liczbowego dla każdego certyfikatu, a indeksy nx_secure_tls_local_certificate_add oparte na nazwie pospolitej X.509. Lokalne usługi certyfikatów stanowią wygodną alternatywę dla identyfikatora liczbowego dla aplikacji, które używają tylko jednego certyfikatu tożsamości — dzięki użyciu nazwy pospolitej aplikacja nie musi śledzić identyfikatorów liczbowych.*</span><span class="sxs-lookup"><span data-stu-id="e9bb8-340">*This API should not be used with the same TLS session when using nx_secure_tls_server_certificate_add. The server certificate API uses a unique numeric identifier for each certificate, and nx_secure_tls_local_certificate_add indexes based on the X.509 Common Name. The local certificate services provide a convenient alternative to the numeric identifier for applications that use only a single identity certificate – by using the Common Name, the application need not keep track of numeric identifiers.*</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-341">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-341">Parameters</span></span>

- <span data-ttu-id="e9bb8-342">**session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-342">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="e9bb8-343">**certificate_ptr** Wskaźnik do zainicjowanych wystąpień certyfikatu TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-343">**certificate_ptr** Pointer to an initialized TLS Certificate instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-344">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-344">Return Values</span></span>

- <span data-ttu-id="e9bb8-345">**NX_SUCCESS** (0x00) Pomyślne dodanie certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-345">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="e9bb8-346">**NX_INVALID_PARAMETERS** (0x4D) Próbowano dodać nieprawidłowy lub zduplikowany certyfikat.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-346">**NX_INVALID_PARAMETERS** (0x4D) Tried to add an invalid or duplicate certificate.</span></span>
- <span data-ttu-id="e9bb8-347">**NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji lub certyfikatu TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-347">**NX_PTR_ERROR** (0x07) Invalid TLS session or certificate pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-348">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-348">Allowed From</span></span>

<span data-ttu-id="e9bb8-349">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-349">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-350">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-350">Example</span></span>

```C
/* Initialize certificate structure. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-351">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-351">See Also</span></span>

- <span data-ttu-id="e9bb8-352">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="e9bb8-352">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="e9bb8-353">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="e9bb8-353">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="e9bb8-354">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="e9bb8-354">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="e9bb8-355">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="e9bb8-355">nx_secure_tls_local_certificate_remove</span></span>
- <span data-ttu-id="e9bb8-356">nx_secure_tls_local_certificate_find</span><span class="sxs-lookup"><span data-stu-id="e9bb8-356">nx_secure_tls_local_certificate_find</span></span>

## <a name="nx_secure_tls_local_certificate_find"></a><span data-ttu-id="e9bb8-357">nx_secure_tls_local_certificate_find</span><span class="sxs-lookup"><span data-stu-id="e9bb8-357">nx_secure_tls_local_certificate_find</span></span>

<span data-ttu-id="e9bb8-358">Znajdowanie certyfikatu lokalnego w bezpiecznej sesji TLS netx według nazwy pospolitej</span><span class="sxs-lookup"><span data-stu-id="e9bb8-358">Find a local certificate in a NetX Secure TLS Session by Common Name</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-359">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-359">Prototype</span></span>

```C
UINT  nx_secure_tls_local_certificate_find(NX_SECURE_TLS_SESSION
                        *session_ptr, NX_SECURE_X509_CERT
                        **certificate, UCHAR *common_name, UINT
                        name_length);
```

### <a name="description"></a><span data-ttu-id="e9bb8-360">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-360">Description</span></span>

<span data-ttu-id="e9bb8-361">Ta usługa znajduje certyfikat w magazynie certyfikatów urządzenia lokalnego sesji TLS i zwraca wskaźnik do struktury NX_SECURE_X509_CERT w magazynie.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-361">This service finds a certificate in the local device certificate store of a TLS session and returns a pointer to the NX_SECURE_X509_CERT structure in the store.</span></span> <span data-ttu-id="e9bb8-362">Parametr common_name i jego długość (name_length) są używane do identyfikowania certyfikatu w magazynie przez dopasowanie pola pospolita X.509 certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-362">The common_name parameter and it's length (name_length) are used to identify the certificate in the store by matching the certificate's X.509 Subject Common Name field.</span></span>

<span data-ttu-id="e9bb8-363">Jeśli istnieje więcej niż jeden certyfikat o tej samej nazwie pospolitej, zostanie zwrócony tylko pierwszy certyfikat — zamiast tego użyj *nx_secure_tls_server_certificate_find* pospolitej.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-363">If more than one certificate with the same Common Name is present, only the first one will be returned – use *nx_secure_tls_server_certificate_find* instead.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e9bb8-364">*Tego interfejsu API nie należy używać z tą samą sesją TLS podczas korzystania z nx_secure_tls_server_certificate_add. Interfejs API certyfikatu serwera używa unikatowego identyfikatora liczbowego dla każdego certyfikatu i nx_secure_tls_local_certificate_add na podstawie nazwy pospolitej X.509. Lokalne usługi certyfikatów stanowią wygodną alternatywę dla identyfikatora liczbowego dla aplikacji, które używają tylko jednego certyfikatu tożsamości — przy użyciu nazwy pospolitej aplikacja nie musi śledzić identyfikatorów liczbowych.*</span><span class="sxs-lookup"><span data-stu-id="e9bb8-364">*This API should not be used with the same TLS session when using nx_secure_tls_server_certificate_add. The server certificate API uses a unique numeric identifier for each certificate, and nx_secure_tls_local_certificate_add indexes based on the X.509 Common Name. The local certificate services provide a convenient alternative to the numeric identifier for applications that use only a single identity certificate – by using the Common Name, the application need not keep track of numeric identifiers.*</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-365">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-365">Parameters</span></span>

- <span data-ttu-id="e9bb8-366">**session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-366">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="e9bb8-367">**certyfikat** Zwraca wskaźnik do dopasowanego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-367">**certificate** Return Pointer to matched certificate.</span></span>
- <span data-ttu-id="e9bb8-368">**common_name** Ciąg nazwy pospolitej do dopasowania (nazwa DNS).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-368">**common_name** Common Name string to match (DNS name).</span></span>
- <span data-ttu-id="e9bb8-369">**name_length** Długość common_name ciągu tekstowego.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-369">**name_length** Length of common_name string data.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-370">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-370">Return Values</span></span>

- <span data-ttu-id="e9bb8-371">**NX_SUCCESS** (0x00) Znaleziono certyfikat i zwrócono wskaźnik w parametrze "certificate".</span><span class="sxs-lookup"><span data-stu-id="e9bb8-371">**NX_SUCCESS** (0x00) Certificate was found and pointer returned in "certificate" parameter.</span></span>
- <span data-ttu-id="e9bb8-372">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Nie znaleziono certyfikatu z podaną nazwą pospolitą.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-372">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate with the supplied Common Name was found.</span></span>
- <span data-ttu-id="e9bb8-373">**NX_PTR_ERROR** (0x07) Nieprawidłowa sesja TLS, wskaźnik certyfikatu lub ciąg nazwy pospolitej.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-373">**NX_PTR_ERROR** (0x07) Invalid TLS session, certificate pointer, or common name string.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-374">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-374">Allowed From</span></span>

<span data-ttu-id="e9bb8-375">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-375">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-376">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-376">Example</span></span>

```C
NX_SECURE_X509_CERT *certificate_ptr;

/* Initialize certificate structure. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */

status = nx_secure_tls_local_certificate_find(&tls_session, &certificate_ptr,
                                      “common name”, strlen(“common name”));

/* If status is NX_SUCCESS the variable “certificate_ptr” points to a certificate
   structure containing a certificate with the Common Name “common name”. */
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-377">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-377">See Also</span></span>

- <span data-ttu-id="e9bb8-378">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="e9bb8-378">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="e9bb8-379">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="e9bb8-379">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="e9bb8-380">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="e9bb8-380">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="e9bb8-381">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="e9bb8-381">nx_secure_tls_local_certificate_remove</span></span>
- <span data-ttu-id="e9bb8-382">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="e9bb8-382">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_local_certificate_remove"></a><span data-ttu-id="e9bb8-383">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="e9bb8-383">nx_secure_tls_local_certificate_remove</span></span>

<span data-ttu-id="e9bb8-384">Usuwanie certyfikatu lokalnego z bezpiecznej sesji TLS netx</span><span class="sxs-lookup"><span data-stu-id="e9bb8-384">Remove local certificate from NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-385">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-385">Prototype</span></span>

```C
UINT  nx_secure_tls_local_certificate_remove(NX_SECURE_TLS_SESSION
                  *session_ptr, UCHAR *common_name, UINT
                  common_name_length);
```

### <a name="description"></a><span data-ttu-id="e9bb8-386">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-386">Description</span></span>

<span data-ttu-id="e9bb8-387">Ta usługa usuwa lokalne wystąpienie certyfikatu z sesji TLS z kluczem w polu Nazwa pospolita w certyfikacie.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-387">This service removes a local certificate instance from a TLS session, keyed on the Common Name field in the certificate.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e9bb8-388">*Tego interfejsu API nie należy używać z tą samą sesją TLS podczas korzystania z nx_secure_tls_server_certificate_add. Interfejs API certyfikatu serwera używa unikatowego identyfikatora liczbowego dla każdego certyfikatu i nx_secure_tls_local_certificate_add na podstawie nazwy pospolitej X.509. Lokalne usługi certyfikatów stanowią wygodną alternatywę dla identyfikatora liczbowego dla aplikacji, które używają tylko jednego certyfikatu tożsamości — przy użyciu nazwy pospolitej aplikacja nie musi śledzić identyfikatorów liczbowych.*</span><span class="sxs-lookup"><span data-stu-id="e9bb8-388">*This API should not be used with the same TLS session when using nx_secure_tls_server_certificate_add. The server certificate API uses a unique numeric identifier for each certificate, and nx_secure_tls_local_certificate_add indexes based on the X.509 Common Name. The local certificate services provide a convenient alternative to the numeric identifier for applications that use only a single identity certificate – by using the Common Name, the application need not keep track of numeric identifiers.*</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-389">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-389">Parameters</span></span>

- <span data-ttu-id="e9bb8-390">**session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-390">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="e9bb8-391">**common_name** Wartość nazwa pospolita certyfikatu do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-391">**common_name** The Common Name value of the certificate to be removed.</span></span>
- <span data-ttu-id="e9bb8-392">**common_name_length** Długość ciągu nazwy pospolitej.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-392">**common_name_length** The length of the Common Name string.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-393">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-393">Return Values</span></span>

- <span data-ttu-id="e9bb8-394">**NX_SUCCESS** (0x00) Pomyślne dodanie certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-394">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="e9bb8-395">**NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-395">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="e9bb8-396">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Nie znaleziono certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-396">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Certificate was not found.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-397">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-397">Allowed From</span></span>

<span data-ttu-id="e9bb8-398">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-398">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-399">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-399">Example</span></span>

```C
/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_remove(&tls_session,
                                                “www.example.com”, 15);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-400">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-400">See Also</span></span>

- <span data-ttu-id="e9bb8-401">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="e9bb8-401">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="e9bb8-402">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="e9bb8-402">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="e9bb8-403">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="e9bb8-403">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="e9bb8-404">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="e9bb8-404">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_metadata_size_calculate"></a><span data-ttu-id="e9bb8-405">nx_secure_tls_metadata_size_calculate</span><span class="sxs-lookup"><span data-stu-id="e9bb8-405">nx_secure_tls_metadata_size_calculate</span></span>

<span data-ttu-id="e9bb8-406">Obliczanie rozmiaru metadanych kryptograficznych dla bezpiecznej sesji TLS NetX</span><span class="sxs-lookup"><span data-stu-id="e9bb8-406">Calculate size of cryptographic metadata for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-407">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-407">Prototype</span></span>

```C
UINT  nx_secure_tls_metadata_size_calculate(
                        const NX_SECURE_TLS_CRYPTO *crypto_table,
                        ULONG *metadata_size);
```

### <a name="description"></a><span data-ttu-id="e9bb8-408">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-408">Description</span></span>

<span data-ttu-id="e9bb8-409">Ta usługa oblicza i zwraca rozmiar metadanych kryptograficznych wymaganych dla określonej sesji TLS i tabeli kryptografii TLS (zobacz sekcję "Inicjowanie szyfrowania TLS za pomocą metod kryptograficznych", aby uzyskać więcej informacji na temat tabeli szyfrowania kryptograficznego).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-409">This service calculates and returns the size of the cryptographic metadata needed for a particular TLS session and TLS cryptography table (see the section "Initializing TLS with Cryptographic Methods" for more information on the cryptographic cipher table).</span></span>

<span data-ttu-id="e9bb8-410">Ta usługa powinna być wywoływana z żądaną tabelą kryptograficznymi, aby obliczyć rozmiar buforu metadanych przekazanego do nx_secure_tls_session_create.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-410">This service should be called with the desired cryptographic table to calculate the size of the metadata buffer passed into nx_secure_tls_session_create.</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-411">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-411">Parameters</span></span>

- <span data-ttu-id="e9bb8-412">**crypto_table** Wskaźnik do pełnej tabeli kryptografii NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-412">**crypto_table** Pointer to a complete NetX Secure TLS cryptography table.</span></span>
- <span data-ttu-id="e9bb8-413">**metadata_size** Dane wyjściowe obliczenia rozmiaru w bajtach.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-413">**metadata_size** The output of the size calculation in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-414">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-414">Return Values</span></span>

- <span data-ttu-id="e9bb8-415">**NX_SUCCESS** (0x00) Pomyślne obliczenie rozmiaru metadanych.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-415">**NX_SUCCESS** (0x00) Successful calculation of metadata size.</span></span>
- <span data-ttu-id="e9bb8-416">**NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik rozmiaru lub tabeli kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-416">**NX_PTR_ERROR** (0x07) Invalid crypto table or return size pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-417">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-417">Allowed From</span></span>

<span data-ttu-id="e9bb8-418">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-418">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-419">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-419">Example</span></span>

```C
/* Pointer to the platform-specific cipher table. */
extern nx_crypto_tls_ciphers;

/* Return variable for metadata size. */
ULONG crypto_metadata_size;

/* Calculate metadata size.  */
status =  nx_secure_tls_metadata_size_calculate(&nx_crypto_tls_ciphers,
                                                &crypto_metadata_size);


/* If status is NX_SUCCESS then crypto_metadata_size contains the size of the
   metadata buffer for the table nx_crypto_tls_ciphers.  */
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-420">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-420">See Also</span></span>

- <span data-ttu-id="e9bb8-421">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="e9bb8-421">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_packet_allocate"></a><span data-ttu-id="e9bb8-422">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="e9bb8-422">nx_secure_tls_packet_allocate</span></span>

<span data-ttu-id="e9bb8-423">Przydzielanie pakietu dla sesji protokołu NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="e9bb8-423">Allocate a packet for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-424">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-424">Prototype</span></span>

```C
UINT  nx_secure_tls_packet_allocate(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET_POOL *pool_ptr,
                                    NX_PACKET **packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="e9bb8-425">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-425">Description</span></span>

<span data-ttu-id="e9bb8-426">Ta usługa przydziela NX_PACKET dla określonej aktywnej sesji TLS z określonego NX_PACKET_POOL.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-426">This service allocates an NX_PACKET for the specified active TLS session from the specified NX_PACKET_POOL.</span></span> <span data-ttu-id="e9bb8-427">Ta usługa powinna zostać wywołana przez aplikację, aby przydzielić pakiety danych do wysłania za pośrednictwem połączenia TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-427">This service should be called by the application to allocate data packets to be sent over a TLS connection.</span></span> <span data-ttu-id="e9bb8-428">Sesja TLS musi zostać zainicjowana przed wywołaniem tej usługi.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-428">The TLS session must be initialized before calling this service.</span></span>

<span data-ttu-id="e9bb8-429">Przydzielony pakiet jest prawidłowo zainicjowany, dzięki czemu dane nagłówka i stopki protokołu TLS mogą zostać dodane po wypełnieniu danych pakietu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-429">The allocated packet is properly initialized so that TLS header and footer data may be added after the packet data is populated.</span></span> <span data-ttu-id="e9bb8-430">W przeciwnym razie zachowanie jest identyczne *nx_packet_allocate*.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-430">The behavior is otherwise identical to *nx_packet_allocate*.</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-431">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-431">Parameters</span></span>

- <span data-ttu-id="e9bb8-432">**session_ptr** Wskaźnik do wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-432">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="e9bb8-433">**pool_ptr** Wskaźnik do NX_PACKET_POOL, z którego ma być przydzielany pakiet.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-433">**pool_ptr** Pointer to an NX_PACKET_POOL from which to allocate the packet.</span></span>
- <span data-ttu-id="e9bb8-434">**packet_ptr** Wskaźnik wyjściowy do nowo przydzielonego pakietu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-434">**packet_ptr** Output pointer to the newly-allocated packet.</span></span>
- <span data-ttu-id="e9bb8-435">**wait_option** Opcja zawieszenia dla alokacji pakietów.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-435">**wait_option** Suspension option for packet allocation.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-436">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-436">Return Values</span></span>

- <span data-ttu-id="e9bb8-437">**NX_SUCCESS** (0x00) Pomyślne przydzielanie pakietów.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-437">**NX_SUCCESS** (0x00) Successful packet allocate.</span></span>
- <span data-ttu-id="e9bb8-438">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Alokacja pakietów bazowych nie powiodła się.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-438">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Underlying packet allocation failed.</span></span>
- <span data-ttu-id="e9bb8-439">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) Dostarczona sesja TLS nie została zainicjowana.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-439">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-440">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-440">Allowed From</span></span>

<span data-ttu-id="e9bb8-441">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-441">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-442">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-442">Example</span></span>

```C
/* Allocate a new TLS packet from the previously created packet pool and
previously initialized TLS session.   */

status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &packet_ptr,
                                       NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
variable packet_ptr.  */
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-443">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-443">See Also</span></span>

- <span data-ttu-id="e9bb8-444">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="e9bb8-444">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="e9bb8-445">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="e9bb8-445">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="e9bb8-446">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="e9bb8-446">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="e9bb8-447">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="e9bb8-447">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="e9bb8-448">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="e9bb8-448">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="e9bb8-449">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="e9bb8-449">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="e9bb8-450">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="e9bb8-450">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="e9bb8-451">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="e9bb8-451">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="e9bb8-452">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="e9bb8-452">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_psk_add"></a><span data-ttu-id="e9bb8-453">nx_secure_tls_psk_add</span><span class="sxs-lookup"><span data-stu-id="e9bb8-453">nx_secure_tls_psk_add</span></span>

<span data-ttu-id="e9bb8-454">Dodawanie klucza wstępnego do bezpiecznej sesji TLS netx</span><span class="sxs-lookup"><span data-stu-id="e9bb8-454">Add a Pre-Shared Key to a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-455">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-455">Prototype</span></span>

```C
UINT  nx_secure_tls_psk_add(NX_SECURE_TLS_SESSION *session_ptr,
                            UCHAR *pre_shared_key, UINT psk_length,
                            UCHAR *psk_identity, UINT
                            identity_length, UCHAR *hint, UINT
                            hint_length);
```

### <a name="description"></a><span data-ttu-id="e9bb8-456">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-456">Description</span></span>

<span data-ttu-id="e9bb8-457">Ta usługa dodaje klucz wstępny , jego ciąg tożsamości i wskazówkę tożsamości do bloku kontroli sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-457">This service adds a Pre-Shared Key (PSK), its identity string, and an identity hint to a TLS Session control block.</span></span> <span data-ttu-id="e9bb8-458">Jeśli są włączone i używane szyfry PSK, używany jest certyfikat cyfrowy, a nie certyfikat cyfrowy.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-458">The PSK is used in place of a digital certificate when PSK ciphersuites are enabled and used.</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-459">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-459">Parameters</span></span>

- <span data-ttu-id="e9bb8-460">**session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-460">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="e9bb8-461">**pre_shared_key** Rzeczywista wartość PSK.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-461">**pre_shared_key** The actual PSK value.</span></span>
- <span data-ttu-id="e9bb8-462">**psk_length** Długość wartości PSK.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-462">**psk_length** The length of the PSK value.</span></span>
- <span data-ttu-id="e9bb8-463">**psk_identity** Ciąg używany do identyfikowania tej wartości PSK.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-463">**psk_identity** A string used to identify this PSK value.</span></span>
- <span data-ttu-id="e9bb8-464">**identity_length** Długość tożsamości psk.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-464">**identity_length** The length of the PSK identity.</span></span>
- <span data-ttu-id="e9bb8-465">**wskazówka** Ciąg używany do wskazywania grupy psk do wyboru na serwerze TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-465">**hint** A string used to indicate which group of PSKs to choose from on a TLS server.</span></span>
- <span data-ttu-id="e9bb8-466">**hint_length** Długość ciągu wskazówki.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-466">**hint_length** The length of the hint string.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-467">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-467">Return Values</span></span>

- <span data-ttu-id="e9bb8-468">**NX_SUCCESS** (0x00) Pomyślne dodanie psk.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-468">**NX_SUCCESS** (0x00) Successful addition of PSK.</span></span>
- <span data-ttu-id="e9bb8-469">**NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-469">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="e9bb8-470">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Nie można dodać kolejnego psk.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-470">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125)  Cannot add another PSK.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-471">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-471">Allowed From</span></span>

<span data-ttu-id="e9bb8-472">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-472">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-473">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-473">Example</span></span>

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to TLS session.  */
status =  nx_secure_tls_psk_add(&tls_session, psk, sizeof(psk), “psk_1”, 4,
“Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-474">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-474">See Also</span></span>

- <span data-ttu-id="e9bb8-475">nx_secure_tls_client_psk_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-475">nx_secure_tls_client_psk_set</span></span>
- <span data-ttu-id="e9bb8-476">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="e9bb8-476">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="e9bb8-477">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="e9bb8-477">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="e9bb8-478">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="e9bb8-478">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="e9bb8-479">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="e9bb8-479">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_remote_certificate_allocate"></a><span data-ttu-id="e9bb8-480">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="e9bb8-480">nx_secure_tls_remote_certificate_allocate</span></span>

<span data-ttu-id="e9bb8-481">Przydzielanie miejsca dla certyfikatu dostarczonego przez zdalnego hosta TLS</span><span class="sxs-lookup"><span data-stu-id="e9bb8-481">Allocate space for the certificate provided by a remote TLS host</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-482">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-482">Prototype</span></span>

```C
UINT  nx_secure_tls_remote_certificate_allocate(
                 NX_SECURE_TLS_SESSION *session_ptr,
                 NX_SECURE_X509_CERT *certificate_ptr,
                 UCHAR *raw_certificate_buffer,
                 UINT raw_buffer_size);
```

### <a name="description"></a><span data-ttu-id="e9bb8-483">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-483">Description</span></span>

<span data-ttu-id="e9bb8-484">Ta usługa dodaje niezainicjowane wystąpienie struktury NX_SECURE_X509_CERT do sesji TLS w celu przydzielenia miejsca na certyfikaty udostępniane przez hosta zdalnego podczas sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-484">This service adds an uninitialized NX_SECURE_X509_CERT structure instance to a TLS session for the purpose of allocating space for certificates provided by a remote host during a TLS session.</span></span> <span data-ttu-id="e9bb8-485">Dane certyfikatu zdalnego są analizowane przez funkcję NetX Secure TLS i te informacje są używane do wypełnienia wystąpienia struktury certyfikatu dostarczonego do tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-485">The remote certificate data is parsed by NetX Secure TLS and that information is used to populate the certificate structure instance provided to this function.</span></span> <span data-ttu-id="e9bb8-486">Certyfikaty dodane w ten sposób są umieszczane na połączonej liście.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-486">Certificates added in this manner are placed in a linked list.</span></span>

<span data-ttu-id="e9bb8-487">Jeśli oczekuje się, że host zdalny udostępni wiele certyfikatów, ta funkcja powinna być wywoływana wielokrotnie, aby przydzielić miejsce dla wszystkich certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-487">If it is expected that the remote host will provide multiple certificates, this function should be called repeatedly to allocate space for all certificates.</span></span> <span data-ttu-id="e9bb8-488">Dodatkowe certyfikaty są dodawane na końcu połączonej listy certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-488">The additional certificates are added to the end of the certificate linked list.</span></span>

<span data-ttu-id="e9bb8-489">Nie można przydzielić certyfikatu zdalnego spowoduje, że tryb klienta TLS nie powiedzie się podczas ugody TLS, chyba że jest w użyciu klucz wstępny (PSK).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-489">Failure to allocate a remote certificate will cause TLS Client mode to fail during the TLS handshake unless a Pre-Shared Key (PSK) ciphersuite is in use.</span></span>

<span data-ttu-id="e9bb8-490">Parametr *raw_certificate_buffer* wskazuje miejsce przydzielone do przechowywania przychodzącego certyfikatu zdalnego.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-490">The *raw_certificate_buffer* parameter points to space allocated to store the incoming remote certificate.</span></span> <span data-ttu-id="e9bb8-491">Typowe certyfikaty z kluczami RSA 2048 bitów używające sha-256 dla podpisów są w zakresie od 1000 do 2000 bajtów.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-491">Typical certificates with RSA keys of 2048 bits using SHA-256 for signatures are in the range of 1000-2000 bytes.</span></span> <span data-ttu-id="e9bb8-492">Bufor powinien być wystarczająco duży, aby co najmniej pomieścić ten rozmiar, ale w zależności od certyfikatów hosta zdalnego może być znacznie mniejszy lub większy.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-492">The buffer should be large enough to at least hold that size, but depending on the remote host certificates may be significantly smaller or larger.</span></span> <span data-ttu-id="e9bb8-493">Należy pamiętać, że jeśli bufor jest zbyt mały do przechowywania certyfikatu przychodzącego, uściślenie TLS zakończy się błędem.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-493">Note that if the buffer is too small to hold the incoming certificate, the TLS handshake will end with an error.</span></span>

<span data-ttu-id="e9bb8-494">W trybie serwera TLS zdalna alokacja certyfikatu jest potrzebna tylko wtedy, gdy jest włączone uwierzytelnianie certyfikatu klienta.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-494">For TLS Server mode, a remote certificate allocation is needed only if client certificate authentication is enabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-495">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-495">Parameters</span></span>

- <span data-ttu-id="e9bb8-496">**session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-496">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="e9bb8-497">**certificate_ptr** Wskaźnik do niezainicjowanych wystąpień certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-497">**certificate_ptr** Pointer to an uninitialized X.509 Certificate instance.</span></span>
- <span data-ttu-id="e9bb8-498">**raw_certificate_buffer** Wskaźnik do buforu do przechowywania nieza analizowanych certyfikatów odebranych z hosta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-498">**raw_certificate_buffer** Pointer to a buffer to hold the un-parsed certificate received from the remote host.</span></span>
- <span data-ttu-id="e9bb8-499">**raw_buffer_size** Rozmiar nieprzetworzowego bufora certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-499">**raw_buffer_size** Size of the raw certificate buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-500">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-500">Return Values</span></span>

- <span data-ttu-id="e9bb8-501">**NX_SUCCESS** (0x00) Pomyślna alokacja certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-501">**NX_SUCCESS** (0x00) Successful allocation of certificate.</span></span>
- <span data-ttu-id="e9bb8-502">**NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-502">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="e9bb8-503">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) Podany bufor był zbyt mały.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-503">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) The supplied buffer was too small.</span></span>
- <span data-ttu-id="e9bb8-504">**NX_INVALID_PARAMETERS** (0x4D) Próbowano dodać nieprawidłowy certyfikat.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-504">**NX_INVALID_PARAMETERS** (0x4D) Tried to add an invalid certificate.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-505">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-505">Allowed From</span></span>

<span data-ttu-id="e9bb8-506">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-506">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-507">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-507">Example</span></span>

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;

/* Buffer space to hold the incoming certificate. */
UCHAR certificate_buffer[2000];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_allocate(&tls_session, &certificate,
                                                    certificate_buffer,
                                                    sizeof(certificate_buffer));


/* If status is NX_SUCCESS the certificate was successfully allocated.  */
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-508">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-508">See Also</span></span>

- <span data-ttu-id="e9bb8-509">nx_secure_x509_certificate_initialize,</span><span class="sxs-lookup"><span data-stu-id="e9bb8-509">nx_secure_x509_certificate_initialize,</span></span>
- <span data-ttu-id="e9bb8-510">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="e9bb8-510">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_remote_certificate_buffer_allocate"></a><span data-ttu-id="e9bb8-511">nx_secure_tls_remote_certificate_buffer_allocate</span><span class="sxs-lookup"><span data-stu-id="e9bb8-511">nx_secure_tls_remote_certificate_buffer_allocate</span></span>

<span data-ttu-id="e9bb8-512">Przydzielanie miejsca dla wszystkich certyfikatów dostarczonych przez zdalnego hosta TLS</span><span class="sxs-lookup"><span data-stu-id="e9bb8-512">Allocate space for all certificates provided by a remote TLS host</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-513">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-513">Prototype</span></span>

```C
UINT  nx_secure_tls_remote_certificate_buffer_allocate(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="e9bb8-514">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-514">Description</span></span>

<span data-ttu-id="e9bb8-515">Ta usługa przydziela miejsce na przetwarzanie łańcuchów certyfikatów przychodzących z hostów serwerów zdalnych w celu przeprowadzenia uwierzytelniania i weryfikacji X.509 w wystąpieniu klienta TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-515">This service allocates space to process incoming certificate chains from remote server hosts in order to perform X.509 authentication and verification in a TLS Client instance.</span></span> <span data-ttu-id="e9bb8-516">W trybie serwera TLS zdalna alokacja certyfikatów jest potrzebna tylko wtedy, gdy jest włączone uwierzytelnianie certyfikatu X.509 klienta — w przypadku wystąpień serwera TLS należy zamiast tego użyć nx_secure_tls_session_x509_client_verify_configure *certyfikatu.*</span><span class="sxs-lookup"><span data-stu-id="e9bb8-516">For TLS Server mode, remote certificate allocation is needed only if client X.509 certificate authentication is enabled – for TLS Server instances the service *nx_secure_tls_session_x509_client_verify_configure* should be used instead.</span></span>

<span data-ttu-id="e9bb8-517">Nie można przydzielić certyfikatów zdalnych spowoduje, że tryb klienta TLS będzie się nie powiódł podczas uściśnia TLS, chyba że jest w użyciu klucz wstępny (PSK).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-517">Failure to allocate remote certificates will cause TLS Client mode to fail during the TLS handshake unless a Pre-Shared Key (PSK) ciphersuite is in use.</span></span>

<span data-ttu-id="e9bb8-518">Parametr *certificate_buffer* wskazuje miejsce przydzielone do przechowywania przychodzących certyfikatów zdalnych oraz bloki sterowania wymagane dla tych certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-518">The *certificate_buffer* parameter points to space allocated to store the incoming remote certificates and the control blocks needed for those certificates.</span></span> <span data-ttu-id="e9bb8-519">Bufor zostanie podzielony przez liczbę certyfikatów *(certs_number*) z równą częścią nadaną każdemu certyfikatowi.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-519">The buffer will be divided by the number of certificates (*certs_number*) with an equal portion given to each certificate.</span></span> <span data-ttu-id="e9bb8-520">Parametr *buffer_size*  wskazuje rozmiar buforu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-520">The *buffer_size*  parameter indicates the size of the buffer.</span></span> <span data-ttu-id="e9bb8-521">Potrzebne miejsce można znaleźć przy użyciu następującej formuły:</span><span class="sxs-lookup"><span data-stu-id="e9bb8-521">The space needed can be found with the following formula:</span></span>

```C
buffer_size = (<expected max number of certificates in chain>) *
                 (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

<span data-ttu-id="e9bb8-522">Typowe certyfikaty z kluczami RSA 2048 bitów używające sha-256 dla podpisów są w zakresie od 1000 do 2000 bajtów.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-522">Typical certificates with RSA keys of 2048 bits using SHA-256 for signatures are in the range of 1000-2000 bytes.</span></span> <span data-ttu-id="e9bb8-523">Bufor powinien być wystarczająco duży, aby pomieścić co najmniej ten rozmiar dla każdego certyfikatu, ale w zależności od certyfikatów hosta zdalnego może być znacznie mniejszy lub większy.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-523">The buffer should be large enough to at least hold that size for each certificate, but depending on the remote host certificates may be significantly smaller or larger.</span></span> <span data-ttu-id="e9bb8-524">Należy pamiętać, że jeśli bufor jest zbyt mały do przechowywania certyfikatu przychodzącego, uściślenie TLS zakończy się błędem.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-524">Note that if the buffer is too small to hold the incoming certificate, the TLS handshake will end with an error.</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-525">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-525">Parameters</span></span>

- <span data-ttu-id="e9bb8-526">**session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-526">**session_ptr** Pointer to a previously created TLS Session  instance.</span></span>
- <span data-ttu-id="e9bb8-527">**certs_number** Liczba certyfikatów do przydzielenia z podanego buforu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-527">**certs_number** Number of certificates to allocate from the  provided buffer.</span></span>
- <span data-ttu-id="e9bb8-528">**certificate_buffer** Wskaźnik do buforu do przechowywania certyfikatów odebranych z hosta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-528">**certificate_buffer** Pointer to a buffer to hold certificates received  from a remote host.</span></span>
- <span data-ttu-id="e9bb8-529">**buffer_size** Rozmiar buforu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-529">**buffer_size** Size of the certificate buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-530">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-530">Return Values</span></span>

- <span data-ttu-id="e9bb8-531">**NX_SUCCESS** (0x00) Pomyślne przydzielenie certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-531">**NX_SUCCESS** (0x00) Successful allocation of certificate.</span></span>
- <span data-ttu-id="e9bb8-532">**NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji lub buforu TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-532">**NX_PTR_ERROR** (0x07) Invalid TLS session or buffer pointer.</span></span>
- <span data-ttu-id="e9bb8-533">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) Podany bufor był zbyt mały.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-533">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) The supplied buffer was too small.</span></span>
- <span data-ttu-id="e9bb8-534">**NX_INVALID_PARAMETERS** (0x4D) Bufor był zbyt mały, aby pomieścić żądaną liczbę certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-534">**NX_INVALID_PARAMETERS** (0x4D) The buffer was too small to hold  the desired number of certificates.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-535">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-535">Allowed From</span></span>

<span data-ttu-id="e9bb8-536">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-536">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-537">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-537">Example</span></span>

```C
/* Buffer space to hold the incoming certificates. */
#define CERTIFICATE_NUMBER    (2)
#define CERTIFICATE_SIZE      (2000)
#define BUFFER_SIZE           (CERTIFICATE_NUMBER * \
                              (sizeof(NX_SECURE_X509_CERT) + CERTIFICATE_SIZE))
UCHAR certificate_buffer[BUFFER_SIZE];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_buffer_allocate(&tls_session,
                                                      CERTIFICATE_NUMBER,
                                                      certificate_buffer,
                                                      BUFFER_SIZE);


/* If status is NX_SUCCESS the buffer was successfully allocated.  */
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-538">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-538">See Also</span></span>

- <span data-ttu-id="e9bb8-539">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="e9bb8-539">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="e9bb8-540">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="e9bb8-540">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_remote_certificate_free_all"></a><span data-ttu-id="e9bb8-541">nx_secure_tls_remote_certificate_free_all</span><span class="sxs-lookup"><span data-stu-id="e9bb8-541">nx_secure_tls_remote_certificate_free_all</span></span>

<span data-ttu-id="e9bb8-542">Wolne miejsce przydzielone dla certyfikatów przychodzących</span><span class="sxs-lookup"><span data-stu-id="e9bb8-542">Free space allocated for incoming certificates</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-543">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-543">Prototype</span></span>

```C
UINT  nx_secure_tls_remote_certificate_free_all(
                  NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="e9bb8-544">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-544">Description</span></span>

<span data-ttu-id="e9bb8-545">Ta usługa służy do wolnej wszystkich buforów certyfikatów przydzielonych do określonej sesji TLS przez nx_secure_tls_remote_certificate_allocated przez zwrócenie ich do wolnego miejsca na certyfikat tej sesji.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-545">This service is used to free all of the certificate buffers allocated to a particular TLS Session by nx_secure_tls_remote_certificate_allocated by returning them to that session's free certificate space.</span></span> <span data-ttu-id="e9bb8-546">Może to być konieczne, jeśli aplikacja ponownie używa obiektu sesji TLS bez usuwania go i ponownego nx_secure_tls_session_delete i nx_secure_tls_session_create.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-546">This may be necessary if an application reuses a TLS session object without deleting it and recreating it with nx_secure_tls_session_delete and nx_secure_tls_session_create.</span></span>

<span data-ttu-id="e9bb8-547">Należy pamiętać, że miejsce na zdalnym certyfikacie jest odzyskiwane automatycznie, gdy sesja TLS jest resetowana zgodnie z nx_secure_tls_session_end, więc większość aplikacji nie powinna wymagać wywołania tej usługi.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-547">Note that the remote certificate space is recovered automatically when the TLS session is reset as happens in nx_secure_tls_session_end so most applications should not need to call this service.</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-548">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-548">Parameters</span></span>

- <span data-ttu-id="e9bb8-549">**session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-549">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-550">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-550">Return Values</span></span>

- <span data-ttu-id="e9bb8-551">**NX_SUCCESS** (0x00) Pomyślna operacja.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-551">**NX_SUCCESS** (0x00) Successful operation.</span></span>
- <span data-ttu-id="e9bb8-552">**NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-552">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="e9bb8-553">**NX_INVALID_PARAMETERS** (0x4D) Błąd wewnętrzny — magazyn certyfikatów jest prawdopodobnie uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-553">**NX_INVALID_PARAMETERS** (0x4D) Internal error – certificate store likely corrupt.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-554">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-554">Allowed From</span></span>

<span data-ttu-id="e9bb8-555">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-555">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-556">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-556">Example</span></span>

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;

/* Buffer space to hold the incoming certificate. */
UCHAR certificate_buffer[2000];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_allocate(&tls_session, &certificate,
                                                    certificate_buffer,
                                                    sizeof(certificate_buffer));


/* If status is NX_SUCCESS the certificate was successfully allocated.  */

/* … TLS session setup, TCP connection, etc… */

/* End TLS session. */
nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);

/* Free up certificate buffers for next connection. */
nx_secure_tls_remote_certificate_free_all(&tls_session);
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-557">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-557">See Also</span></span>

- <span data-ttu-id="e9bb8-558">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="e9bb8-558">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="e9bb8-559">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="e9bb8-559">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="e9bb8-560">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="e9bb8-560">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="e9bb8-561">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="e9bb8-561">nx_secure_tls_session_end</span></span>

## <a name="nx_secure_tls_server_certificate_add"></a><span data-ttu-id="e9bb8-562">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="e9bb8-562">nx_secure_tls_server_certificate_add</span></span>

<span data-ttu-id="e9bb8-563">Dodawanie certyfikatu przeznaczonego specjalnie dla serwerów TLS przy użyciu identyfikatora liczbowego</span><span class="sxs-lookup"><span data-stu-id="e9bb8-563">Add a certificate specifically for TLS servers using a numeric identifier</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-564">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-564">Prototype</span></span>

```C
UINT  nx_secure_tls_server_certificate_add(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  NX_SECURE_X509_CERT *certificate, UINT cert_id);
```

### <a name="description"></a><span data-ttu-id="e9bb8-565">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-565">Description</span></span>

<span data-ttu-id="e9bb8-566">Ta usługa służy do dodawania certyfikatu do magazynu lokalnego sesji TLS (zobacz nx_secure_tls_local_certificate_add) przy użyciu identyfikatora liczbowego zamiast indeksowania magazynu przy użyciu podmiotu X.509 (nazwa pospolita) w certyfikacie.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-566">This service is used to add a certificate to a TLS session's local store (see nx_secure_tls_local_certificate_add) using a numeric identifier instead of indexing the store using the X.509 Subject (Common Name) within the certificate.</span></span> <span data-ttu-id="e9bb8-567">Identyfikator liczbowy jest oddzielony od certyfikatu i umożliwia dodanie wielu certyfikatów jako certyfikatów tożsamości do serwera TLS, a także umożliwia dodanie wielu certyfikatów o tej samej nazwie pospolitej do tego samego magazynu lokalnego sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-567">The numeric identifier is separate from the certificate and allows multiple certificates to be added as identity certificates to a TLS server, as well as allowing multiple certificates with the same Common Name to be added to the same TLS session local store.</span></span> <span data-ttu-id="e9bb8-568">Ta sama usługa może być używana w przypadku certyfikatów klienta, ale rzadko klient TLS ma wiele certyfikatów tożsamości.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-568">This same service can be used for client certificates, but it is rare for a TLS client to have multiple identity certificates.</span></span>

<span data-ttu-id="e9bb8-569">Parametr cert_id jest niezerową dodatnią liczbą całkowitą przypisaną przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-569">The cert_id parameter is a non-zero positive integer assigned by the application.</span></span> <span data-ttu-id="e9bb8-570">Rzeczywista wartość nie ma znaczenia (innej niż zero), ale musi być unikatowa w magazynie dla podanej sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-570">The actual value does not matter (other than zero) but it must be unique in the store for the provided TLS session.</span></span> <span data-ttu-id="e9bb8-571">Wartość cert_id może służyć do znalezienia i usunięcia certyfikatów z magazynu lokalnego przy użyciu nx_secure_tls_server_certificate_find i nx_secure_tls_server_certificate_remove.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-571">The cert_id value can be used to find and remove certificates from the local store using nx_secure_tls_server_certificate_find and nx_secure_tls_server_certificate_remove, respectively.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e9bb8-572">*Tego interfejsu API nie należy używać z tą samą sesją TLS podczas korzystania z nx_secure_tls_local_certificate_add. Interfejs API nx_secure_tls_server_certificate_add używa unikatowego identyfikatora liczbowego dla każdego certyfikatu i indeksu lokalnych usług certyfikatów na podstawie nazwy pospolitej X.509. Usługi certyfikatów serwera umożliwiają istnienia wielu certyfikatów z danymi udostępnionym (szczególnie nazwa pospolita) w tym samym magazynie lokalnym — jest to przydatne w przypadku serwera z wieloma tożsamościami.*</span><span class="sxs-lookup"><span data-stu-id="e9bb8-572">*This API should not be used with the same TLS session when using nx_secure_tls_local_certificate_add. The nx_secure_tls_server_certificate_add API uses a unique numeric identifier for each certificate, and local certificate services index based on the X.509 Common Name. The server certificate services allow multiple certificates with shared data (especially Common Name) to exist in the same local store – this is useful for a server with multiple identities.*</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-573">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-573">Parameters</span></span>

- <span data-ttu-id="e9bb8-574">**session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-574">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="e9bb8-575">**certyfikat** Wskaźnik do wcześniej zainicjowane wystąpienie certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-575">**certificate** Pointer to a previously initialized X.509 certificate instance.</span></span>
- <span data-ttu-id="e9bb8-576">**cert_id** Dodatni, niezerowy, stosunkowo unikatowy numer identyfikatora certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-576">**cert_id** Positive, non-zero, relatively unique certificate ID number.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-577">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-577">Return Values</span></span>

- <span data-ttu-id="e9bb8-578">**NX_SUCCESS** (0x00)Operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-578">**NX_SUCCESS** (0x00)Successful operation.</span></span>
- <span data-ttu-id="e9bb8-579">**NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji lub certyfikatu TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-579">**NX_PTR_ERROR** (0x07) Invalid TLS session orcertificate pointer.</span></span>
- <span data-ttu-id="e9bb8-580">**NX_SECURE_TLS_CERT_ID_INVALID** (0x138) Podany identyfikator certyfikatu miał nieprawidłową wartość (prawdopodobnie 0).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-580">**NX_SECURE_TLS_CERT_ID_INVALID** (0x138) The provided certificate ID had An invalid value (likely 0).</span></span>
- <span data-ttu-id="e9bb8-581">**NX_SECURE_TLS_CERT_ID_DUPLICATE** (0x139) Podany identyfikator certyfikatu był już obecny w magazynie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-581">**NX_SECURE_TLS_CERT_ID_DUPLICATE** (0x139) The provided certificate ID was already present in the local store.</span></span>
- <span data-ttu-id="e9bb8-582">**NX_INVALID_PARAMETERS(0x4D)** Błąd wewnętrzny — magazyn certyfikatów jest prawdopodobnie uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-582">**NX_INVALID_PARAMETERS(0x4D)** Internal error – certificate store likely corrupt.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-583">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-583">Allowed From</span></span>

<span data-ttu-id="e9bb8-584">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-584">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-585">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-585">Example</span></span>

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;


/* Add certificate to TLS session.  */
status =  nx_secure_tls_server_certificate_add(&tls_session, &certificate, 0x12);


/* If status is NX_SUCCESS the certificate was successfully added with the ID
0x12.  */
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-586">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-586">See Also</span></span>

- <span data-ttu-id="e9bb8-587">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="e9bb8-587">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="e9bb8-588">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="e9bb8-588">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="e9bb8-589">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-589">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="e9bb8-590">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="e9bb8-590">nx_secure_tls_server_certificate_find</span></span>
- <span data-ttu-id="e9bb8-591">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="e9bb8-591">nx_secure_tls_server_certificate_remove</span></span>

## <a name="nx_secure_tls_server_certificate_find"></a><span data-ttu-id="e9bb8-592">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="e9bb8-592">nx_secure_tls_server_certificate_find</span></span>

<span data-ttu-id="e9bb8-593">Znajdowanie certyfikatu przy użyciu identyfikatora liczbowego</span><span class="sxs-lookup"><span data-stu-id="e9bb8-593">Find a certificate using a numeric identifier</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-594">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-594">Prototype</span></span>

```C
UINT  nx_secure_tls_server_certificate_find(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  NX_SECURE_X509_CERT **certificate, UINT cert_id);
```

### <a name="description"></a><span data-ttu-id="e9bb8-595">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-595">Description</span></span>

<span data-ttu-id="e9bb8-596">Ta usługa służy do wyszukiwania certyfikatu w magazynie lokalnym sesji TLS (zobacz nx_secure_tls_local_certificate_add) przy użyciu identyfikatora liczbowego zamiast indeksowania magazynu przy użyciu podmiotu X.509 (nazwa pospolita) w certyfikacie.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-596">This service is used to find a certificate in a TLS session's local store (see nx_secure_tls_local_certificate_add) using a numeric identifier instead of indexing the store using the X.509 Subject (Common Name) within the certificate.</span></span>

<span data-ttu-id="e9bb8-597">Parametr cert_id jest niezerową dodatnią liczbą całkowitą przypisaną przez aplikację po dodaniu certyfikatu do lokalnego magazynu sesji TLS przy użyciu nx_secure_tls_server_certificate_add.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-597">The cert_id parameter is a non-zero positive integer assigned by the application when the certificate is added to the TLS session local store using nx_secure_tls_server_certificate_add.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e9bb8-598">*Tego interfejsu API nie należy używać z tą samą sesją TLS podczas korzystania z nx_secure_tls_local_certificate_add. Interfejs API nx_secure_tls_server_certificate_add używa unikatowego identyfikatora liczbowego dla każdego certyfikatu i indeksu lokalnych usług certyfikatów na podstawie nazwy pospolitej X.509. Usługi certyfikatów serwera umożliwiają wielu certyfikatom z danymi udostępnionym (zwłaszcza nazwą pospolitą) istniejące w tym samym magazynie lokalnym — jest to przydatne w przypadku serwera z wieloma tożsamościami.*</span><span class="sxs-lookup"><span data-stu-id="e9bb8-598">*This API should not be used with the same TLS session when using nx_secure_tls_local_certificate_add. The nx_secure_tls_server_certificate_add API uses a unique numeric identifier for each certificate, and local certificate services index based on the X.509 Common Name. The server certificate services allow multiple certificates with shared data (especially Common Name) to exist in the same local store – this is useful for a server with multiple identities.*</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-599">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-599">Parameters</span></span>

- <span data-ttu-id="e9bb8-600">**session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-600">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="e9bb8-601">**certyfikat** Wskaźnik do wskaźnika certyfikatu X.509 w celu zwrócenia odwołania do znalezionego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-601">**certificate** Pointer to an X.509 certificate pointer to return a reference to the found certificate.</span></span>
- <span data-ttu-id="e9bb8-602">**cert_id** Niezerowa dodatnia wartość identyfikatora certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-602">**cert_id** Non-zero positive certificate ID value.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-603">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-603">Return Values</span></span>

- <span data-ttu-id="e9bb8-604">**NX_SUCCESS** (0x00)Operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-604">**NX_SUCCESS** (0x00)Successful operation.</span></span>
- <span data-ttu-id="e9bb8-605">**NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji lub certyfikatu TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-605">**NX_PTR_ERROR** (0x07) Invalid TLS session or certificate pointer.</span></span>
- <span data-ttu-id="e9bb8-606">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Podany identyfikator certyfikatu nie pasuje do żadnego z identyfikatorów w magazynie lokalnym podanej sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-606">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) The provided certificate ID did not match any in the local store of the provided TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-607">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-607">Allowed From</span></span>

<span data-ttu-id="e9bb8-608">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-608">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-609">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-609">Example</span></span>

```C
NX_SECURE_X509_CERT *certificate;


/* Find certificate in TLS session.  */
status =  nx_secure_tls_server_certificate_find(&tls_session, &certificate, 0x12);


/* If status is NX_SUCCESS the certificate was successfully found and a reference
returned in the certificate parameter.  */
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-610">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-610">See Also</span></span>

- <span data-ttu-id="e9bb8-611">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="e9bb8-611">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="e9bb8-612">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="e9bb8-612">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="e9bb8-613">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-613">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="e9bb8-614">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="e9bb8-614">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="e9bb8-615">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="e9bb8-615">nx_secure_tls_server_certificate_remove</span></span>

##  <a name="nx_secure_tls_server_certificate_remove"></a><span data-ttu-id="e9bb8-616">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="e9bb8-616">nx_secure_tls_server_certificate_remove</span></span>

<span data-ttu-id="e9bb8-617">Usuwanie certyfikatu serwera lokalnego przy użyciu identyfikatora liczbowego</span><span class="sxs-lookup"><span data-stu-id="e9bb8-617">Remove a local server certificate using a numeric identifier</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-618">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-618">Prototype</span></span>

```C
UINT  nx_secure_tls_server_certificate_remove(
                  NX_SECURE_TLS_SESSION *session_ptr, UINT cert_id);
```

### <a name="description"></a><span data-ttu-id="e9bb8-619">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-619">Description</span></span>

<span data-ttu-id="e9bb8-620">Ta usługa służy do usuwania certyfikatu z magazynu lokalnego sesji TLS (zobacz nx_secure_tls_local_certificate_add) przy użyciu identyfikatora liczbowego zamiast indeksowania magazynu przy użyciu podmiotu X.509 (nazwa pospolita) w certyfikacie.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-620">This service is used to remove a certificate from a TLS session's local store (see nx_secure_tls_local_certificate_add) using a numeric identifier instead of indexing the store using the X.509 Subject (Common Name) within the certificate.</span></span>

<span data-ttu-id="e9bb8-621">Parametr cert_id jest niezerową dodatnią liczbą całkowitą przypisaną przez aplikację po dodaniu certyfikatu do lokalnego magazynu sesji TLS przy użyciu nx_secure_tls_server_certificate_add.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-621">The cert_id parameter is a non-zero positive integer assigned by the application when the certificate is added to the TLS session local store using nx_secure_tls_server_certificate_add.</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-622">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-622">Parameters</span></span>

- <span data-ttu-id="e9bb8-623">**session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-623">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="e9bb8-624">**cert_id** Niezerowa dodatnia wartość identyfikatora certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-624">**cert_id** Non-zero positive certificate ID value.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-625">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-625">Return Values</span></span>

- <span data-ttu-id="e9bb8-626">**NX_SUCCESS** (0x00)Operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-626">**NX_SUCCESS** (0x00)Successful operation.</span></span>
- <span data-ttu-id="e9bb8-627">**NX_PTR_ERROR** (0x07) Nieprawidłowa sesja TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-627">**NX_PTR_ERROR** (0x07) Invalid TLS session.</span></span>
- <span data-ttu-id="e9bb8-628">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Podany identyfikator certyfikatu nie pasuje do żadnego z identyfikatorów w magazynie lokalnym podanej sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-628">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) The provided certificate ID did not match any in the local store of the provided TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-629">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-629">Allowed From</span></span>

<span data-ttu-id="e9bb8-630">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-630">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-631">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-631">Example</span></span>

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;


/* Add certificate to TLS session with id 0x12.  */
status =  nx_secure_tls_server_certificate_add(&tls_session, &certificate, 0x12);
/* Use certificate in TLS session, etc… */

/* Remove certificate from TLS session with id 0x12.  */
status =  nx_secure_tls_server_certificate_remove(&tls_session, 0x12);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-632">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-632">See Also</span></span>

- <span data-ttu-id="e9bb8-633">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="e9bb8-633">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="e9bb8-634">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="e9bb8-634">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="e9bb8-635">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-635">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="e9bb8-636">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="e9bb8-636">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="e9bb8-637">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="e9bb8-637">nx_secure_tls_server_certificate_find</span></span>

## <a name="nx_secure_tls_session_alert_value_get"></a><span data-ttu-id="e9bb8-638">nx_secure_tls_session_alert_value_get</span><span class="sxs-lookup"><span data-stu-id="e9bb8-638">nx_secure_tls_session_alert_value_get</span></span>

<span data-ttu-id="e9bb8-639">Uzyskiwanie wartości i poziomu alertu TLS wysyłanych przez hosta zdalnego</span><span class="sxs-lookup"><span data-stu-id="e9bb8-639">Get the TLS alert value and level sent by the remote host</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-640">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-640">Prototype</span></span>

```C
UINT  nx_secure_tls_session_alert_value_get(
                   NX_SECURE_TLS_SESSION *session_ptr,
                   UINT *alert_level, UINT *alert_value);
```

### <a name="description"></a><span data-ttu-id="e9bb8-641">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-641">Description</span></span>

<span data-ttu-id="e9bb8-642">Ta usługa służy do pobierania wartości i poziomu alertu TLS, gdy host zdalny wysyła alert w odpowiedzi na jakiś problem lub błąd.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-642">This service is used to retrieve the TLS alert level and value when the remote host sends an alert in response to some problem or error.</span></span>

<span data-ttu-id="e9bb8-643">Wartości parametrów alert_level i alert_value są prawidłowe tylko wtedy, gdy ta funkcja jest wywoływana natychmiast po wywołaniu interfejsu API TLS, które zwróciło stan NX_SECURE_TLS_ALERT_RECEIVED (0x114) wskazujący, że otrzymano alert z hosta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-643">The values of the alert_level and alert_value parameters are only valid if this function is called immediately following a TLS API call that returned a status of NX_SECURE_TLS_ALERT_RECEIVED (0x114) indicating that an alert was received from the remote host.</span></span>

<span data-ttu-id="e9bb8-644">Należy pamiętać, że jeśli lokalny host TLS wysyła alert, zwrócone kody błędów są znacznie bardziej opisowe dla rzeczywistego błędu niż sam alert TLS, ponieważ wartości alertów TLS celowo pozostawiają niejednoznaczne, aby zapobiec niektórym typom ataków (takim jak atak typu "wyrocznia wypełnienia" lub podobne).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-644">Note that if the local host TLS sends an alert, the returned error codes are far more descriptive of the actual error than the TLS alert itself because TLS alert values are intentionally left ambiguous to prevent certain types of attack (such as a "padding oracle" attack or similar).</span></span>

<span data-ttu-id="e9bb8-645">Poziom alertu przyjmuje tylko jedną z dwóch wartości: NX_SECURE_TLS_ALERT_LEVEL_WARNING (0x1) lub NX_SECURE_TLS_ALERT_LEVEL_FATAL (0x2).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-645">The alert level only takes one of two values: NX_SECURE_TLS_ALERT_LEVEL_WARNING (0x1) or NX_SECURE_TLS_ALERT_LEVEL_FATAL (0x2).</span></span> <span data-ttu-id="e9bb8-646">Ogólnie rzecz biorąc, tylko alert CloseNotify (używany do wskazania pomyślnego zakończenia sesji TLS) będzie miał poziom "Ostrzeżenie", chociaż niektóre sytuacje konfiguracji rozszerzenia mogą również być traktowane jako ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-646">In general, only the CloseNotify Alert (used to indicate a successful end to a TLS session) will be given a level of "Warning" though some extension configuration situations may also be considered warnings.</span></span> <span data-ttu-id="e9bb8-647">Ogromna większość alertów będzie "Krytyczny" wskazujący potencjalny błąd zabezpieczeń i skutkować natychmiastowym zamknięciem połączenia TLS (ugoda lub sesja).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-647">The vast majority of alerts will be "Fatal" indicating a potential security failure and resulting in immediate closure of the TLS connection (handshake or session).</span></span>

<span data-ttu-id="e9bb8-648">Wartości alertów TLS są zdefiniowane w dokumencie RFC 5246 (TLSv1.2) w dokumencie RLS. Poniżej znajduje się lista referencyjna:</span><span class="sxs-lookup"><span data-stu-id="e9bb8-648">The TLS alert values are defined in the TLS RFCs, here is the list from RFC 5246 (TLSv1.2) for reference:</span></span>

| <span data-ttu-id="e9bb8-649">Nazwa alertu</span><span class="sxs-lookup"><span data-stu-id="e9bb8-649">Alert Name</span></span>                     | <span data-ttu-id="e9bb8-650">Wartość</span><span class="sxs-lookup"><span data-stu-id="e9bb8-650">Value</span></span> | <span data-ttu-id="e9bb8-651">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-651">Description</span></span>                                                                                                                                                  |
| ---------------------------------- | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="e9bb8-652">close_notify</span><span class="sxs-lookup"><span data-stu-id="e9bb8-652">close_notify</span></span>                  | <span data-ttu-id="e9bb8-653">0</span><span class="sxs-lookup"><span data-stu-id="e9bb8-653">0</span></span>     | <span data-ttu-id="e9bb8-654">Brak błędu, oznacza pomyślne zakończenie sesji</span><span class="sxs-lookup"><span data-stu-id="e9bb8-654">No error, indicates successful session end</span></span>                                                                                                                   |
| <span data-ttu-id="e9bb8-655">unexpected_message</span><span class="sxs-lookup"><span data-stu-id="e9bb8-655">unexpected_message</span></span>            | <span data-ttu-id="e9bb8-656">10</span><span class="sxs-lookup"><span data-stu-id="e9bb8-656">10</span></span>    | <span data-ttu-id="e9bb8-657">TLS odebrał nieoczekiwany lub nieodpowiedny komunikat</span><span class="sxs-lookup"><span data-stu-id="e9bb8-657">TLS received an unexpected or out-of-order message</span></span>                                                                                                           |
| <span data-ttu-id="e9bb8-658">bad_record_mac</span><span class="sxs-lookup"><span data-stu-id="e9bb8-658">bad_record_mac</span></span>               | <span data-ttu-id="e9bb8-659">20</span><span class="sxs-lookup"><span data-stu-id="e9bb8-659">20</span></span>    | <span data-ttu-id="e9bb8-660">Odszyfrowywanie i/lub weryfikacja adresu MAC nie powiodła się</span><span class="sxs-lookup"><span data-stu-id="e9bb8-660">Decryption and/or MAC verification failed</span></span>                                                                                                                    |
| <span data-ttu-id="e9bb8-661">decryption_failed_RESERVED</span><span class="sxs-lookup"><span data-stu-id="e9bb8-661">decryption_failed_RESERVED</span></span>   | <span data-ttu-id="e9bb8-662">21</span><span class="sxs-lookup"><span data-stu-id="e9bb8-662">21</span></span>    | <span data-ttu-id="e9bb8-663">**PRZESTARZAŁE** Odszyfrowywanie nie powiodło się (jest przestarzałe z powodu ataków na wyrocznię uzupełniania)</span><span class="sxs-lookup"><span data-stu-id="e9bb8-663">**DEPRECATED** Decryption failed (deprecated due to padding oracle attacks)</span></span>                                                                                      |
| <span data-ttu-id="e9bb8-664">record_overflow</span><span class="sxs-lookup"><span data-stu-id="e9bb8-664">record_overflow</span></span>               | <span data-ttu-id="e9bb8-665">22</span><span class="sxs-lookup"><span data-stu-id="e9bb8-665">22</span></span>    | <span data-ttu-id="e9bb8-666">Odebrano rekord, który jest większy niż maksymalny rozmiar rekordu TLS</span><span class="sxs-lookup"><span data-stu-id="e9bb8-666">A record was received that is larger than the TLS maximum record size</span></span>                                                                                        |
| <span data-ttu-id="e9bb8-667">decompression_failure</span><span class="sxs-lookup"><span data-stu-id="e9bb8-667">decompression_failure</span></span>         | <span data-ttu-id="e9bb8-668">30</span><span class="sxs-lookup"><span data-stu-id="e9bb8-668">30</span></span>    | <span data-ttu-id="e9bb8-669">Wystąpił problem podczas kompresji/dekompresji rekordu TLS</span><span class="sxs-lookup"><span data-stu-id="e9bb8-669">A problem was encountered in compression/decompression of a TLS record</span></span>                                                                                       |
| <span data-ttu-id="e9bb8-670">handshake_failure</span><span class="sxs-lookup"><span data-stu-id="e9bb8-670">handshake_failure</span></span>             | <span data-ttu-id="e9bb8-671">40</span><span class="sxs-lookup"><span data-stu-id="e9bb8-671">40</span></span>    | <span data-ttu-id="e9bb8-672">Wystąpił nieokreślony błąd uściślinia, który nie jest objęty innym alertem</span><span class="sxs-lookup"><span data-stu-id="e9bb8-672">Some unspecified handshake error occurred that isn't covered by a different alert</span></span>                                                                            |
| <span data-ttu-id="e9bb8-673">no_certificate_RESERVED</span><span class="sxs-lookup"><span data-stu-id="e9bb8-673">no_certificate_RESERVED</span></span>      | <span data-ttu-id="e9bb8-674">41</span><span class="sxs-lookup"><span data-stu-id="e9bb8-674">41</span></span>    | <span data-ttu-id="e9bb8-675">**PRZESTARZAŁE w** protokołach TLS (tylko protokół SSL)</span><span class="sxs-lookup"><span data-stu-id="e9bb8-675">**DEPRECATED** in TLS (SSL only)</span></span>                                                                                                                                 |
| <span data-ttu-id="e9bb8-676">bad_certificate</span><span class="sxs-lookup"><span data-stu-id="e9bb8-676">bad_certificate</span></span>               | <span data-ttu-id="e9bb8-677">42</span><span class="sxs-lookup"><span data-stu-id="e9bb8-677">42</span></span>    | <span data-ttu-id="e9bb8-678">Odebrany certyfikat zawiera nieprawidłowe formatowanie lub nieprawidłowe podpisy</span><span class="sxs-lookup"><span data-stu-id="e9bb8-678">A certificate that was received contained invalid formatting or signatures</span></span>                                                                                   |
| <span data-ttu-id="e9bb8-679">unsupported_certificate</span><span class="sxs-lookup"><span data-stu-id="e9bb8-679">unsupported_certificate</span></span>       | <span data-ttu-id="e9bb8-680">43</span><span class="sxs-lookup"><span data-stu-id="e9bb8-680">43</span></span>    | <span data-ttu-id="e9bb8-681">Odebrano certyfikat o nieprawidłowym typie (np. certyfikat tylko do podpisywania używany do uwierzytelniania serwera TLS)</span><span class="sxs-lookup"><span data-stu-id="e9bb8-681">A certificate was received that was of an invalid type (e.g. signing-only certificate used for TLS server authentication)</span></span>                                    |
| <span data-ttu-id="e9bb8-682">certificate_revoked</span><span class="sxs-lookup"><span data-stu-id="e9bb8-682">certificate_revoked</span></span>           | <span data-ttu-id="e9bb8-683">44</span><span class="sxs-lookup"><span data-stu-id="e9bb8-683">44</span></span>    | <span data-ttu-id="e9bb8-684">Stan certyfikatu (dostarczony przez listy CRL lub OCSP) został wskazany jako "odwołany"</span><span class="sxs-lookup"><span data-stu-id="e9bb8-684">The certificate status (as provided by a CRL or OCSP) was indicated as being "revoked"</span></span>                                                                       |
| <span data-ttu-id="e9bb8-685">certificate_expired</span><span class="sxs-lookup"><span data-stu-id="e9bb8-685">certificate_expired</span></span>           | <span data-ttu-id="e9bb8-686">45</span><span class="sxs-lookup"><span data-stu-id="e9bb8-686">45</span></span>    | <span data-ttu-id="e9bb8-687">Odebrany certyfikat był poza prawidłowym zakresem dat (nie jest jeszcze ważny lub wygasł)</span><span class="sxs-lookup"><span data-stu-id="e9bb8-687">The received certificate was outside it's valid date range (either not valid yet or expired)</span></span>                                                                 |
| <span data-ttu-id="e9bb8-688">certificate_unknown</span><span class="sxs-lookup"><span data-stu-id="e9bb8-688">certificate_unknown</span></span>           | <span data-ttu-id="e9bb8-689">46</span><span class="sxs-lookup"><span data-stu-id="e9bb8-689">46</span></span>    | <span data-ttu-id="e9bb8-690">Wystąpił nieznany problem z certyfikatem, który nie był objęty innymi alertami</span><span class="sxs-lookup"><span data-stu-id="e9bb8-690">Some unknown certificate issue was encountered that was not covered by other alerts</span></span>                                                                          |
| <span data-ttu-id="e9bb8-691">illegal_parameter</span><span class="sxs-lookup"><span data-stu-id="e9bb8-691">illegal_parameter</span></span>             | <span data-ttu-id="e9bb8-692">47</span><span class="sxs-lookup"><span data-stu-id="e9bb8-692">47</span></span>    | <span data-ttu-id="e9bb8-693">Niektóre wartości konfiguracji lub negocjowane w uściśliwce TLS były nieprawidłowe lub poza zakresem</span><span class="sxs-lookup"><span data-stu-id="e9bb8-693">Some configuration or negotiated value in the TLS handshake was invalid or out of range</span></span>                                                                      |
| <span data-ttu-id="e9bb8-694">unknown_ca</span><span class="sxs-lookup"><span data-stu-id="e9bb8-694">unknown_ca</span></span>                    | <span data-ttu-id="e9bb8-695">48</span><span class="sxs-lookup"><span data-stu-id="e9bb8-695">48</span></span>    | <span data-ttu-id="e9bb8-696">Nie można śledzić odebranego certyfikatu tożsamości za pośrednictwem łańcucha certyfikatów do certyfikatu zaufanego głównego urzędu certyfikacji.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-696">The received identity certificate could not be traced via a certificate chain to a trusted root CA certificate.</span></span>                                              |
| <span data-ttu-id="e9bb8-697">Access_denied</span><span class="sxs-lookup"><span data-stu-id="e9bb8-697">access_denied</span></span>                 | <span data-ttu-id="e9bb8-698">49</span><span class="sxs-lookup"><span data-stu-id="e9bb8-698">49</span></span>    | <span data-ttu-id="e9bb8-699">Wskazuje, że odebrano prawidłowy certyfikat, ale kontrola dostępu do aplikacji wskazuje, że certyfikat jest nieprawidłowy dla żądanych zasobów.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-699">Indicates a valid certificate was received but application access control indicated that the certificate was invalid for the requested resources.</span></span>            |
| <span data-ttu-id="e9bb8-700">decode_error</span><span class="sxs-lookup"><span data-stu-id="e9bb8-700">decode_error</span></span>                  | <span data-ttu-id="e9bb8-701">50</span><span class="sxs-lookup"><span data-stu-id="e9bb8-701">50</span></span>    | <span data-ttu-id="e9bb8-702">Niektóre pola lub wartości w nagłówku lub komunikacie uściślniania TLS były poza zakresem lub nieprawidłowe, co prowadziło do błędu dekodowania rekordu TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-702">Some field or value in a TLS header or handshake message was out of range or invalid, leading to a failure in decoding of a TLS record.</span></span>                      |
| <span data-ttu-id="e9bb8-703">decrypt_error</span><span class="sxs-lookup"><span data-stu-id="e9bb8-703">decrypt_error</span></span>                 | <span data-ttu-id="e9bb8-704">51</span><span class="sxs-lookup"><span data-stu-id="e9bb8-704">51</span></span>    | <span data-ttu-id="e9bb8-705">Nie można zweryfikować skrótu podpisu lub zakończonego komunikatu podczas ugody TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-705">A signature or Finished message hash during the TLS handshake could not be verified.</span></span>                                                                         |
| <span data-ttu-id="e9bb8-706">export_restriction_RESERVED</span><span class="sxs-lookup"><span data-stu-id="e9bb8-706">export_restriction_RESERVED</span></span>  | <span data-ttu-id="e9bb8-707">60</span><span class="sxs-lookup"><span data-stu-id="e9bb8-707">60</span></span>    | <span data-ttu-id="e9bb8-708">PRZESTARZAŁE W TLSv1.2</span><span class="sxs-lookup"><span data-stu-id="e9bb8-708">DEPRECATED in TLSv1.2</span></span>                                                                                                                                        |
| <span data-ttu-id="e9bb8-709">protocol_version</span><span class="sxs-lookup"><span data-stu-id="e9bb8-709">protocol_version</span></span>              | <span data-ttu-id="e9bb8-710">70</span><span class="sxs-lookup"><span data-stu-id="e9bb8-710">70</span></span>    | <span data-ttu-id="e9bb8-711">Wersja protokołu TLS negocjowana podczas procesu uzgodnienia jest rozpoznawana, ale nie jest obsługiwana (np. TLSv1.0 została przedstawiona, ale nie włączona).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-711">The TLS protocol version negotiated during the handshake is recognized but not supported (e.g. TLSv1.0 was presented but not enabled).</span></span>                       |
| <span data-ttu-id="e9bb8-712">insufficient_security</span><span class="sxs-lookup"><span data-stu-id="e9bb8-712">insufficient_security</span></span>         | <span data-ttu-id="e9bb8-713">71</span><span class="sxs-lookup"><span data-stu-id="e9bb8-713">71</span></span>    | <span data-ttu-id="e9bb8-714">Wysyłane za każdym razem, gdy handshake zakończy się niepowodzeniem z powodu braku bezpiecznych szyfrów (np. rozmiar klucza jest zbyt mały, aby spełnić wymagania aplikacji)</span><span class="sxs-lookup"><span data-stu-id="e9bb8-714">Sent whenever a handshake fails due to a lack of secure ciphers (e.g. key size is too small for the application requirements)</span></span>                                |
| <span data-ttu-id="e9bb8-715">internal_error</span><span class="sxs-lookup"><span data-stu-id="e9bb8-715">internal_error</span></span>                | <span data-ttu-id="e9bb8-716">80</span><span class="sxs-lookup"><span data-stu-id="e9bb8-716">80</span></span>    | <span data-ttu-id="e9bb8-717">Niektóre błędy inne niż TLS (np. problemy z alokacją pamięci, problemy z aplikacją) wystąpiły, co skutkowało przerwaną sesją TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-717">Some non-TLS error (e.g. memory allocation problems, application issues) occurred resulting in a broken TLS session.</span></span>                                         |
| <span data-ttu-id="e9bb8-718">user_canceled</span><span class="sxs-lookup"><span data-stu-id="e9bb8-718">user_canceled</span></span>                 | <span data-ttu-id="e9bb8-719">90</span><span class="sxs-lookup"><span data-stu-id="e9bb8-719">90</span></span>    | <span data-ttu-id="e9bb8-720">Zwracany, jeśli sesja TLS zostanie anulowana przez użytkownika lub aplikację przed zakończeniem procesu handshake (podobnie jak w przypadku closeNotify).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-720">Returned if the TLS session is cancelled by a user or application before the handshake is complete (similar to CloseNotify).</span></span>                                 |
| <span data-ttu-id="e9bb8-721">no_renegotiation</span><span class="sxs-lookup"><span data-stu-id="e9bb8-721">no_renegotiation</span></span>              | <span data-ttu-id="e9bb8-722">100</span><span class="sxs-lookup"><span data-stu-id="e9bb8-722">100</span></span>   | <span data-ttu-id="e9bb8-723">Indietes, że host zdalny nie chce wykonać renegocjacji TLS uściślić w odpowiedzi na żądanie ponownego negocjowania.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-723">Indiates that the remote host is not willing to perform TLS renegotiation handshakes in response to a renegotiation request.</span></span>                                 |
| <span data-ttu-id="e9bb8-724">unsupported_extension</span><span class="sxs-lookup"><span data-stu-id="e9bb8-724">unsupported_extension</span></span>         | <span data-ttu-id="e9bb8-725">110</span><span class="sxs-lookup"><span data-stu-id="e9bb8-725">110</span></span>   | <span data-ttu-id="e9bb8-726">Wysyłane, jeśli klient TLS odbierze serwerHello zawierający rozszerzenia, o które nie pytano jawnie w początkowej aplikacji ClientHello (co wskazuje, że serwer ma problem).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-726">Sent if a TLS Client receives a ServerHello containing extensions not explicitly asked for in the initial ClientHello (indicating the server has a problem).</span></span> |

### <a name="parameters"></a><span data-ttu-id="e9bb8-727">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-727">Parameters</span></span>

- <span data-ttu-id="e9bb8-728">**session_ptr** Wskaźnik do wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-728">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="e9bb8-729">**alert_level** Zwróć poziom odebranego alertu (ostrzeżenie lub błąd krytyczny).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-729">**alert_level** Return the level of the received alert (warning or fatal).</span></span>
- <span data-ttu-id="e9bb8-730">**alert_value** Zwraca wartość odebranego alertu (zobacz tabelę).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-730">**alert_value** Return the value of the received alert (see table).</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-731">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-731">Return Values</span></span>

- <span data-ttu-id="e9bb8-732">**NX_SUCCESS** (0x00) Pomyślna operacja.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-732">**NX_SUCCESS** (0x00) Successful operation.</span></span>
- <span data-ttu-id="e9bb8-733">**NX_PTR_ERROR** (0x07) Nieprawidłowa sesja TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-733">**NX_PTR_ERROR** (0x07) Invalid TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-734">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-734">Allowed From</span></span>

<span data-ttu-id="e9bb8-735">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-735">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-736">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-736">Example</span></span>

```C
/* Return values. */
UINT status, alert_level, alert_value;


/* Start a TLS session.  */
status =  nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);

/* Check for “alert received” error. */
if(status == NX_SECURE_TLS_ALERT_RECEIVED)
{

        /* Get the alert level and value. */
        status =  nx_secure_tls_session_alert_value_get(&tls_session,
                                             &alert_level, &alert_value);

        /* Print out the received alert level and value. */
        printf("Alert recieved. Value: %d, Level: %d\n", alert_value,
                alert_level);
}
else if(status != NX_SUCCESS)
{
    /* Additional error handling. */
}
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-737">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-737">See Also</span></span>

- <span data-ttu-id="e9bb8-738">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="e9bb8-738">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="e9bb8-739">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="e9bb8-739">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="e9bb8-740">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="e9bb8-740">nx_secure_tls_session_receive</span></span>

## <a name="nx_secure_tls_session_certificate_callback_set"></a><span data-ttu-id="e9bb8-741">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-741">nx_secure_tls_session_certificate_callback_set</span></span>

<span data-ttu-id="e9bb8-742">Konfigurowanie wywołania zwrotnego dla usługi TLS na użytek dodatkowej weryfikacji certyfikatu</span><span class="sxs-lookup"><span data-stu-id="e9bb8-742">Set up a callback for TLS to use for additional certificate validation</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-743">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-743">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_certificate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *session,
                                    NX_SECURE_X509_CERT *certificate));
```

### <a name="description"></a><span data-ttu-id="e9bb8-744">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-744">Description</span></span>

<span data-ttu-id="e9bb8-745">Ta usługa przypisuje wskaźnik funkcji do sesji TLS, która będzie wywoływana przez usługę TLS po odebraniu certyfikatu z hosta zdalnego, co umożliwia aplikacji przeprowadzanie testów poprawności, takich jak weryfikacja systemu DNS, odwoływanie certyfikatów i wymuszanie zasad certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-745">This service assigns a function pointer to a TLS session that TLS will invoke when a certificate is received from a remote host, allowing the application to perform validation checks such as DNS validation, certificate revocation, and certificate policy enforcement.</span></span>

<span data-ttu-id="e9bb8-746">Zabezpieczenia NetX TLS będą wykonywać podstawową weryfikację ścieżki X.509 certyfikatu przed wywołaniem wywołania zwrotnego, aby mieć pewność, że certyfikat może być śledzony do certyfikatu w magazynie zaufanych certyfikatów TLS, ale wszystkie pozostałe weryfikacje będą obsługiwane przez to wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-746">NetX Secure TLS will perform basic X.509 path validation on the certificate before invoking the callback to assure that the certificate can be traced to a certificate in the TLS trusted certificate store, but all other validation will be handled by this callback.</span></span>

<span data-ttu-id="e9bb8-747">Wywołanie zwrotne udostępnia wskaźnik sesji TLS i wskaźnik do certyfikatu tożsamości hosta zdalnego (liścia w łańcuchu certyfikatów).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-747">The callback provides the TLS session pointer and a pointer to the remote host identity certificate (the leaf in the certificate chain).</span></span> <span data-ttu-id="e9bb8-748">Wywołanie zwrotne powinno zwrócić NX_SUCCESS, jeśli cała walidacja powiedzie się. W przeciwnym razie powinien zostać zwrócony kod błędu wskazujący niepowodzenie walidacji.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-748">The callback should return NX_SUCCESS if all validation is successful, otherwise it should return an error code indicating the validation failure.</span></span> <span data-ttu-id="e9bb8-749">Każda wartość inna NX_SUCCESS spowoduje natychmiastowe przerwanie uściśniania TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-749">Any value other than NX_SUCCESS will cause the TLS handshake to immediately abort.</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-750">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-750">Parameters</span></span>

- <span data-ttu-id="e9bb8-751">**session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-751">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="e9bb8-752">**func_ptr** Wskaźnik do funkcji wywołania zwrotnego weryfikacji certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-752">**func_ptr** Pointer to the certificate validation callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-753">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-753">Return Values</span></span>

- <span data-ttu-id="e9bb8-754">**NX_SUCCESS** (0x00) Pomyślna alokacja wskaźnika funkcji.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-754">**NX_SUCCESS** (0x00) Successful allocation of Function pointer.</span></span>
- <span data-ttu-id="e9bb8-755">**NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-755">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-756">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-756">Allowed From</span></span>

<span data-ttu-id="e9bb8-757">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-757">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-758">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-758">Example</span></span>

```C
/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
    /* Certificate validation checking goes here. */
    return(NX_SUCCESS);
}

/* In TLS setup routine. */
{
        /* Add callback to TLS session.  */
        status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                            certificate_callback);

        /* If status is NX_SUCCESS the certificate callback was added.  */
}
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-759">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-759">See Also</span></span>

- <span data-ttu-id="e9bb8-760">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="e9bb8-760">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="e9bb8-761">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="e9bb8-761">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="e9bb8-762">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="e9bb8-762">nx_secure_x509_crl_revocation_check</span></span>

## <a name="nx_secure_tls_session_client_callback_set"></a><span data-ttu-id="e9bb8-763">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-763">nx_secure_tls_session_client_callback_set</span></span>

<span data-ttu-id="e9bb8-764">Konfigurowanie wywołania zwrotnego dla usługi TLS do wywoływania na początku uściślniania klienta TLS</span><span class="sxs-lookup"><span data-stu-id="e9bb8-764">Set up a callback for TLS to invoke at the beginning of a TLS Client handshake</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-765">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-765">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_client_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                    NX_SECURE_TLS_HELLO_EXTENSION
                                    *extensions, UINT num_extensions));
```

### <a name="description"></a><span data-ttu-id="e9bb8-766">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-766">Description</span></span>

<span data-ttu-id="e9bb8-767">Ta usługa przypisuje wskaźnik funkcji do sesji TLS, która będzie wywoływana po otrzymaniu komunikatu ServerHelloDone klienta TLS Client.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-767">This service assigns a function pointer to a TLS session that TLS will invoke when a TLS Client handshake has received a ServerHelloDone message.</span></span> <span data-ttu-id="e9bb8-768">Funkcja wywołania zwrotnego umożliwia aplikacji przetwarzanie wszelkich rozszerzeń TLS z odebranego komunikatu ServerHello, które wymagają danych wejściowych lub podejmowania decyzji.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-768">The callback function allows an application to process any TLS extensions from the received ServerHello message that require input or decision making.</span></span>

<span data-ttu-id="e9bb8-769">Wywołanie zwrotne jest wykonywane przy użyciu wywołującego bloku kontroli sesji TLS i tablicy NX_SECURE_TLS_HELLO_EXTENSION obiektów.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-769">The callback is executed with the invoking TLS session control block and an array of NX_SECURE_TLS_HELLO_EXTENSION objects.</span></span> <span data-ttu-id="e9bb8-770">Tablica obiektów rozszerzenia ma być przekazywana do funkcji pomocnika, która znajdzie i przejmie określone rozszerzenie.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-770">The array of extension objects is intended to be passed into a helper function that will find and parse a specific extension.</span></span> <span data-ttu-id="e9bb8-771">Obecnie w środowisku NetX Secure nie są obsługiwane żadne określone rozszerzenia, które wymagają danych wejściowych klienta TLS, ale wywołanie zwrotne jest dostępne dla projektantów aplikacji w celu obsługi rozszerzeń niestandardowych lub nowych, które mogą stać się dostępne.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-771">Currently, there are no specific extensions supported in NetX Secure that require TLS Client input, but the callback is available for application designers to handle custom or new extensions that may become available.</span></span> <span data-ttu-id="e9bb8-772">Przykładowa funkcja pomocnika, która analizuje rozszerzenia TLS podane w komunikatach powitalnych, zobacz *nx_secure_tls_session_sni_extension_parse*.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-772">For an example helper function that parses TLS extensions provided in hello messages, see *nx_secure_tls_session_sni_extension_parse*.</span></span>

<span data-ttu-id="e9bb8-773">Wywołanie zwrotne klienta może również służyć do wybierania aktywnego certyfikatu tożsamości przy użyciu usługi *nx_secure_tls_active_certificate_set* dla klienta TLS w przypadku, gdy serwer zdalny zażądał certyfikatu i podał informacje umożliwiające klientowi TLS wybranie określonego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-773">The client callback may also be used to select the active identity certificate using *nx_secure_tls_active_certificate_set* for the TLS Client in the event that the remote server has requested a certificate and provided information to allow the TLS Client to select a specific certificate.</span></span> <span data-ttu-id="e9bb8-774">Aby uzyskać więcej informacji, zobacz nx_secure_tls_active_certificate_set informacje.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-774">See the reference for nx_secure_tls_active_certificate_set for more information.</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-775">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-775">Parameters</span></span>

- <span data-ttu-id="e9bb8-776">**session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-776">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="e9bb8-777">**func_ptr** Wskaźnik do funkcji wywołania zwrotnego klienta TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-777">**func_ptr** Pointer to the TLS Client callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-778">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-778">Return Values</span></span>

- <span data-ttu-id="e9bb8-779">**NX_SUCCESS** (0x00) Pomyślna alokacja wskaźnika funkcji.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-779">**NX_SUCCESS** (0x00) Successful allocation of function pointer.</span></span>
- <span data-ttu-id="e9bb8-780">**NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-780">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-781">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-781">Allowed From</span></span>

<span data-ttu-id="e9bb8-782">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-782">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-783">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-783">Example</span></span>

```C
/* Callback routine used to process ServerHello extensions and perform other
   runtime actions at the beginning of a TLS handshake (such as selecting an
   identify certificate to provide to the server). */

ULONG tls_client_callback(NX_SECURE_TLS_SESSION *session,
                          NX_SECURE_TLS_HELLO_EXTENSION *extensions, UINT
                          num_extensions)
{

    /* Extension parsing would go here. */

    /* Set an active identity certificate – the certificate should have been added
       to the local store at application start with
       nx_secure_tls_local_certificate_add. */
    nx_secure_tls_active_certificate_set(session, &global_identity_certificate);

    return(NX_SUCCESS);
}

/* TLS setup routine. */
UINT tls_setup(NX_SECURE_TLS_SESSION *tls_session)
{
    /* Add callback to TLS session.  */
    status =  nx_secure_tls_session_client_callback_set(tls_session,
                                                        client_callback);

    /* If status is NX_SUCCESS the callback was added and will be invoked once
       a ServerHelloDone message is received. */

    return(status);
}
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-784">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-784">See Also</span></span>

- <span data-ttu-id="e9bb8-785">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="e9bb8-785">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="e9bb8-786">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-786">nx_secure_tls_session_server_callback_set</span></span>
- <span data-ttu-id="e9bb8-787">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-787">nx_secure_tls_active_certificate_set</span></span>

## <a name="nx_secure_tls_session_x509_client_verify_configure"></a><span data-ttu-id="e9bb8-788">nx_secure_tls_session_x509_client_verify_configure</span><span class="sxs-lookup"><span data-stu-id="e9bb8-788">nx_secure_tls_session_x509_client_verify_configure</span></span>

<span data-ttu-id="e9bb8-789">Włączanie weryfikacji X.509 klienta i przydzielanie miejsca dla certyfikatów klienta</span><span class="sxs-lookup"><span data-stu-id="e9bb8-789">Enable client X.509 verification and allocate space for client certificates</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-790">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-790">Prototype</span></span>

```C
UINT  nx_secure_tls_session_x509_client_verify_configure(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="e9bb8-791">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-791">Description</span></span>

<span data-ttu-id="e9bb8-792">Ta usługa umożliwia opcjonalne uwierzytelnianie klienta X.509 dla wystąpienia serwera TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-792">This service enables the optional X.509 Client Authentication for a TLS Server instance.</span></span> <span data-ttu-id="e9bb8-793">Przydziela również miejsce potrzebne do przetwarzania łańcuchów certyfikatów przychodzących z hosta klienta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-793">It also allocates the space needed to process incoming certificate chains from the remote client host.</span></span> <span data-ttu-id="e9bb8-794">Certyfikaty dostarczone przez klienta zdalnego zostaną zweryfikowane względem zaufanych certyfikatów wystąpienia serwera TLS przypisanych do usługi *nx_secure_tls_trusted_certificate_add.*</span><span class="sxs-lookup"><span data-stu-id="e9bb8-794">The certificates supplied by the remote client will be verified against the TLS server instance's trusted certificates, assigned with the service *nx_secure_tls_trusted_certificate_add.*</span></span>

<span data-ttu-id="e9bb8-795">W trybie klienta TLS wymagana jest zdalna alokacja certyfikatów, a zamiast *nx_secure_tls_remote_certificate_buffer_allocate* należy użyć usługi.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-795">For TLS Client mode, remote certificate allocation is required and the service *nx_secure_tls_remote_certificate_buffer_allocate* should be used instead.</span></span> <span data-ttu-id="e9bb8-796">Włączenie uwierzytelniania klienta X.509 w wystąpieniu klienta TLS nie będzie mieć żadnego efektu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-796">Enabling X.509 Client Authentication on a TLS Client instance will have no effect.</span></span>

<span data-ttu-id="e9bb8-797">Parametr *certificate_buffer* wskazuje miejsce przydzielone do przechowywania przychodzących certyfikatów zdalnych oraz bloki sterowania wymagane dla tych certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-797">The *certificate_buffer* parameter points to space allocated to store the incoming remote certificates and the control blocks needed for those certificates.</span></span> <span data-ttu-id="e9bb8-798">Bufor zostanie podzielony przez liczbę certyfikatów *(certs_number*) z równą częścią nadaną każdemu certyfikatowi.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-798">The buffer will be divided by the number of certificates (*certs_number*) with an equal portion given to each certificate.</span></span> <span data-ttu-id="e9bb8-799">Parametr *buffer_size* wskazuje rozmiar buforu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-799">The *buffer_size* parameter indicates the size of the buffer.</span></span> <span data-ttu-id="e9bb8-800">Potrzebne miejsce można znaleźć przy użyciu następującej formuły:</span><span class="sxs-lookup"><span data-stu-id="e9bb8-800">The space needed can be found with the following formula:</span></span>

```C
buffer_size = (<expected max number of certificates in chain>) *
             (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

<span data-ttu-id="e9bb8-801">Typowe certyfikaty z kluczami RSA 2048 bitów używające sha-256 dla podpisów są w zakresie od 1000 do 2000 bajtów.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-801">Typical certificates with RSA keys of 2048 bits using SHA-256 for signatures are in the range of 1000-2000 bytes.</span></span> <span data-ttu-id="e9bb8-802">Bufor powinien być wystarczająco duży, aby pomieścić co najmniej ten rozmiar dla każdego certyfikatu, ale w zależności od certyfikatów hosta zdalnego może być znacznie mniejszy lub większy.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-802">The buffer should be large enough to at least hold that size for each certificate, but depending on the remote host certificates may be significantly smaller or larger.</span></span> <span data-ttu-id="e9bb8-803">Należy pamiętać, że jeśli bufor jest zbyt mały do przechowywania certyfikatu przychodzącego, uściślicie TLS zakończy się błędem.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-803">Note that if the buffer is too small to hold the incoming certificate, the TLS handshake will end with an error.</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-804">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-804">Parameters</span></span>

- <span data-ttu-id="e9bb8-805">**session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-805">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="e9bb8-806">**certs_number** Liczba certyfikatów do przydzielenia z podanego buforu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-806">**certs_number** Number of certificates to allocate from the provided buffer.</span></span>
- <span data-ttu-id="e9bb8-807">**certificate_buffer** Wskaźnik do buforu do przechowywania certyfikatów odebranych z hosta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-807">**certificate_buffer** Pointer to a buffer to hold certificates received from a remote host.</span></span>
- <span data-ttu-id="e9bb8-808">**buffer_size** Rozmiar buforu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-808">**buffer_size** Size of the certificate buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-809">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-809">Return Values</span></span>

- <span data-ttu-id="e9bb8-810">**NX_SUCCESS** (0x00)Pomyślna alokacja certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-810">**NX_SUCCESS** (0x00)Successful allocation of certificate.</span></span>
- <span data-ttu-id="e9bb8-811">**NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji lub buforu TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-811">**NX_PTR_ERROR** (0x07) Invalid TLS session or buffer pointer.</span></span>
- <span data-ttu-id="e9bb8-812">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) Podany bufor był zbyt mały.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-812">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) The supplied buffer was too small.</span></span>
- <span data-ttu-id="e9bb8-813">**NX_INVALID_PARAMETERS** (0x4D) Bufor był zbyt mały, aby pomieścić żądaną liczbę certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-813">**NX_INVALID_PARAMETERS** (0x4D) The buffer was too small to hold the desired number of certificates.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-814">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-814">Allowed From</span></span>

<span data-ttu-id="e9bb8-815">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-815">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-816">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-816">Example</span></span>

```C
/* Buffer space to hold the incoming certificates. */
#define CERTIFICATE_NUMBER    (2)
#define CERTIFICATE_SIZE      (2000)
#define BUFFER_SIZE          (CERTIFICATE_NUMBER * \
                                (sizeof(NX_SECURE_X509_CERT) + CERTIFICATE_SIZE))
UCHAR certificate_buffer[BUFFER_SIZE];

/* Enable X.509 Client verification and allocate certificate space in our TLS
   Server session.  */
status =  nx_secure_tls_session_x509_client_verify_configure(&tls_session,
                                                    CERTIFICATE_NUMBER,
                                                    certificate_buffer,
                                                    BUFFER_SIZE);


/* If status is NX_SUCCESS the buffer was successfully allocated.  */
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-817">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-817">See Also</span></span>

- <span data-ttu-id="e9bb8-818">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="e9bb8-818">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="e9bb8-819">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="e9bb8-819">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="e9bb8-820">nx_secure_tls_remote_certificate_buffer_allocate</span><span class="sxs-lookup"><span data-stu-id="e9bb8-820">nx_secure_tls_remote_certificate_buffer_allocate</span></span>

## <a name="nx_secure_tls_session_client_verify_disable"></a><span data-ttu-id="e9bb8-821">nx_secure_tls_session_client_verify_disable</span><span class="sxs-lookup"><span data-stu-id="e9bb8-821">nx_secure_tls_session_client_verify_disable</span></span>

<span data-ttu-id="e9bb8-822">Wyłączanie uwierzytelniania certyfikatu klienta dla sesji protokołu NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="e9bb8-822">Disable Client Certificate Authentication for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-823">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-823">Prototype</span></span>

```C
UINT  nx_secure_tls_session_client_verify_disable(
                              NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="e9bb8-824">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-824">Description</span></span>

<span data-ttu-id="e9bb8-825">Ta usługa wyłącza uwierzytelnianie certyfikatu klienta dla określonej sesji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-825">This service disables Client Certificate Authentication for a specific TLS session.</span></span> <span data-ttu-id="e9bb8-826">Zobacz nx_secure_tls_session_client_verify_enable, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-826">See nx_secure_tls_session_client_verify_enable for more information.</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-827">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-827">Parameters</span></span>

- <span data-ttu-id="e9bb8-828">**session_ptr** Wskaźnik do wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-828">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-829">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-829">Return Values</span></span>

- <span data-ttu-id="e9bb8-830">**NX_SUCCESS** (0x00) Pomyślna zmiana stanu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-830">**NX_SUCCESS** (0x00) Successful state change.</span></span>
- <span data-ttu-id="e9bb8-831">**NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-831">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-832">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-832">Allowed From</span></span>

<span data-ttu-id="e9bb8-833">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-833">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-834">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-834">Example</span></span>

```C
/* Disable client certificate authentication for this TLS session.   */
status = nx_secure_tls_session_client_verify_disable(&tls_session);

/* Any new TLS Server sessions using the tls_session control block will not
request certificates from the remote TLS client.  */
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-835">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-835">See Also</span></span>

- <span data-ttu-id="e9bb8-836">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="e9bb8-836">nx_secure_tls_session_client_verify_enable</span></span>
- <span data-ttu-id="e9bb8-837">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="e9bb8-837">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="e9bb8-838">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="e9bb8-838">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_client_verify_enable"></a><span data-ttu-id="e9bb8-839">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="e9bb8-839">nx_secure_tls_session_client_verify_enable</span></span>

<span data-ttu-id="e9bb8-840">Włączanie uwierzytelniania certyfikatu klienta dla bezpiecznej sesji protokołu TLS netx</span><span class="sxs-lookup"><span data-stu-id="e9bb8-840">Enable Client Certificate Authentication for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-841">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-841">Prototype</span></span>

```C
UINT  nx_secure_tls_session_client_verify_enable(
                                NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="e9bb8-842">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-842">Description</span></span>

<span data-ttu-id="e9bb8-843">Ta usługa umożliwia uwierzytelnianie certyfikatu klienta dla określonej sesji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-843">This service enables Client Certificate Authentication for a specific TLS session.</span></span> <span data-ttu-id="e9bb8-844">Włączenie uwierzytelniania certyfikatu klienta dla wystąpienia serwera TLS spowoduje, że serwer TLS zażąda certyfikatu od dowolnego zdalnego klienta protokołu TLS podczas początkowego uwierzytelniania TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-844">Enabling Client Certificate Authentication for a TLS Server instance will cause the TLS Server to request a certificate from any remote TLS Client during the initial TLS handshake.</span></span> <span data-ttu-id="e9bb8-845">Do certyfikatu otrzymanego od zdalnego klienta TLS jest dołączany komunikat CertificateVerify, którego serwer TLS używa do sprawdzenia, czy klient jest właścicielem certyfikatu (ma dostęp do klucza prywatnego skojarzonego z tym certyfikatem).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-845">The certificate received from the remote TLS Client is accompanied by a CertificateVerify message, which the TLS Server uses to verify that the Client owns the certificate (has access to the private key associated with that certificate).</span></span>

<span data-ttu-id="e9bb8-846">Jeśli dostarczony certyfikat można zweryfikować i prześledzić z powrotem do certyfikatu w magazynie zaufanych certyfikatów serwera TLS za pośrednictwem łańcucha certyfikatów X.509, uwierzytelniany jest zdalny klient TLS i będzie kontynuowane ugodę.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-846">If the provided certificate can be verified and traced back to a certificate in the TLS Server trusted certificate store via an X.509 certificate chain, the remote TLS Client is authenticated and the handshake proceeds.</span></span> <span data-ttu-id="e9bb8-847">W przypadku błędów podczas przetwarzania certyfikatu lub komunikatu CertificateVerify, uściślicie TLS kończy się błędem.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-847">In case of any errors in processing the certificate or CertificateVerify message, the TLS handshake ends with an error.</span></span>

> [!NOTE]
> <span data-ttu-id="e9bb8-848">*Serwer TLS musi mieć w swoim zaufanym magazynie co najmniej jeden certyfikat dodany z nx_secure_tls_trusted_certificate_add w przypadku, gdy uwierzytelnianie zawsze nie powiedzie się.*</span><span class="sxs-lookup"><span data-stu-id="e9bb8-848">*The TLS Server must have at least one certificate in its trusted store added with nx_secure_tls_trusted_certificate_add or authentication will always fail.*</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-849">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-849">Parameters</span></span>

- <span data-ttu-id="e9bb8-850">**session_ptr** Wskaźnik do wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-850">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-851">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-851">Return Values</span></span>

- <span data-ttu-id="e9bb8-852">**NX_SUCCESS** (0x00) Pomyślna zmiana stanu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-852">**NX_SUCCESS** (0x00) Successful state change.</span></span>
- <span data-ttu-id="e9bb8-853">**NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-853">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-854">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-854">Allowed From</span></span>

<span data-ttu-id="e9bb8-855">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-855">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-856">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-856">Example</span></span>

```C
/* Add a trusted certificate so the TLS Server has something to verify against. */
status = nx_secure_tls_trusted_certificate_add(&tls_session,
                                               &trusted_certificate);

/* Disable client certificate authentication for this TLS session.   */
status = nx_secure_tls_session_client_verify_enable(&tls_session);

/* Any new TLS Server sessions using the tls_session control block will now
request and verify certificates from the remote TLS client.  */
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-857">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-857">See Also</span></span>

- <span data-ttu-id="e9bb8-858">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="e9bb8-858">nx_secure_tls_session_client_verify_enable</span></span>
- <span data-ttu-id="e9bb8-859">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="e9bb8-859">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="e9bb8-860">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="e9bb8-860">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="e9bb8-861">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="e9bb8-861">nx_secure_tls_trusted_certificate_add</span></span>

## <a name="nx_secure_tls_session_create"></a><span data-ttu-id="e9bb8-862">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="e9bb8-862">nx_secure_tls_session_create</span></span>

<span data-ttu-id="e9bb8-863">Tworzenie bezpiecznej sesji TLS netx na celu bezpieczną komunikację</span><span class="sxs-lookup"><span data-stu-id="e9bb8-863">Create a NetX Secure TLS Session for secure communications</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-864">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-864">Prototype</span></span>

```C
UINT  nx_secure_tls_session_create(NX_SECURE_TLS_SESSION *session_ptr
                                   NX_SECURE_TLS_CRYPTO *cipher_table,
                                   VOID *encryption_metadata_area,
                                   ULONG encryption_metadata_size);
```

### <a name="description"></a><span data-ttu-id="e9bb8-865">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-865">Description</span></span>

<span data-ttu-id="e9bb8-866">Ta usługa inicjuje wystąpienie NX_SECURE_TLS_SESSION struktury do użycia podczas ustanawiania bezpiecznej komunikacji TLS za pośrednictwem połączenia sieciowego.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-866">This service initializes an NX_SECURE_TLS_SESSION structure instance for use in establishing secure TLS communications over a network connection.</span></span>

<span data-ttu-id="e9bb8-867">Metoda przyjmuje obiekt NX_SECURE_TLS_CRYPTO, który jest wypełniany dostępnymi metodami kryptograficznymi, które mają być używane w przypadku szyfrowania TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-867">The method takes a NX_SECURE_TLS_CRYPTO object that is populated with the available cryptographic methods to be used for TLS.</span></span> <span data-ttu-id="e9bb8-868">Interfejs *encryption_metadata_area* bufor przydzielony do użycia przez usługę TLS dla "metadanych" używanych przez metody kryptograficzne w tabeli NX_SECURE_TLS_CRYPTO do obliczeń.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-868">The *encryption_metadata_area* points to a buffer allocated for use by TLS for the "metadata" used by the cryptographic methods in the NX_SECURE_TLS_CRYPTO table for calculations.</span></span> <span data-ttu-id="e9bb8-869">Rozmiar tabeli można określić przy użyciu usługi nx_secure_tls_metadata_size_calculate service.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-869">The size of the table can be determined by using the nx_secure_tls_metadata_size_calculate service.</span></span> <span data-ttu-id="e9bb8-870">Aby uzyskać więcej informacji, zobacz sekcję "Kryptografia w zabezpieczonych zabezpieczeniach TLS netX" w rozdziale 3.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-870">See the section "Cryptography in NetX Secure TLS" in Chapter 3 for more details.</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-871">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-871">Parameters</span></span>

- <span data-ttu-id="e9bb8-872">**session_ptr** Wskaźnik do wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-872">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="e9bb8-873">**cipher_table** Wskaźnik do metod kryptograficznych TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-873">**cipher_table** Pointer to TLS cryptographic methods.</span></span>
- <span data-ttu-id="e9bb8-874">**encryption_metadata_area** Wskaźnik do miejsca dla metadanych kryptografii.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-874">**encryption_metadata_area** Pointer to space for cryptography metadata.</span></span>
- <span data-ttu-id="e9bb8-875">**encryption_metadata_size** Rozmiar buforu metadanych.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-875">**encryption_metadata_size** Size of the metadata buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-876">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-876">Return Values</span></span>

- <span data-ttu-id="e9bb8-877">**NX_SUCCESS** (0x00)Pomyślne zainicjowanie sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-877">**NX_SUCCESS** (0x00)Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="e9bb8-878">**NX_PTR_ERROR** (0x07) Próbowano użyć nieprawidłowego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-878">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="e9bb8-879">**NX_INVALID_PARAMETERS** (0x4D) Bufor metadanych był zbyt mały dla danej metody.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-879">**NX_INVALID_PARAMETERS** (0x4D) The metadata buffer was too small for the given methods.</span></span>
- <span data-ttu-id="e9bb8-880">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) W tabeli szyfrowania nie połączono wymaganej metody szyfrowania dla włączonej wersji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-880">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) A required cipher method for the enabled version of TLS was not supplied in the cipher table.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-881">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-881">Allowed From</span></span>

<span data-ttu-id="e9bb8-882">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-882">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-883">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-883">Example</span></span>

```C
/* Reference the platform-specific TLS cryptographic method table. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;

/* Declare a buffer for the cryptographic metadata. The size should be calculated
   using nx_secure_tls_metadata_size_calculate. */
UCHAR crypto_metadata[4500];

/* Initialize TLS session.  */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* If status is NX_SUCCESS the TLS Session was successfully initialized.  */
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-884">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-884">See Also</span></span>

- <span data-ttu-id="e9bb8-885">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="e9bb8-885">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="e9bb8-886">nx_secure_tls_metadata_size_calculate</span><span class="sxs-lookup"><span data-stu-id="e9bb8-886">nx_secure_tls_metadata_size_calculate</span></span>
- <span data-ttu-id="e9bb8-887">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="e9bb8-887">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="e9bb8-888">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="e9bb8-888">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="e9bb8-889">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="e9bb8-889">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="e9bb8-890">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="e9bb8-890">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="e9bb8-891">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="e9bb8-891">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="e9bb8-892">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="e9bb8-892">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="e9bb8-893">Kryptografia w zabezpieczonych zabezpieczeniach TLS NetX w rozdziale 3</span><span class="sxs-lookup"><span data-stu-id="e9bb8-893">Cryptography in NetX Secure TLS in Chapter 3</span></span>

## <a name="nx_secure_tls_session_delete"></a><span data-ttu-id="e9bb8-894">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="e9bb8-894">nx_secure_tls_session_delete</span></span>

<span data-ttu-id="e9bb8-895">Usuwanie bezpiecznej sesji TLS netx</span><span class="sxs-lookup"><span data-stu-id="e9bb8-895">Delete a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-896">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-896">Prototype</span></span>

```C
UINT  nx_secure_tls_session_delete(NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="e9bb8-897">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-897">Description</span></span>

<span data-ttu-id="e9bb8-898">Ta usługa usuwa sesję TLS reprezentowaną przez wystąpienie struktury NX_SECURE_TLS_SESSION i zwalnia wszystkie zasoby systemowe należące do tego wystąpienia sesji.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-898">This service deletes a TLS session represented by an NX_SECURE_TLS_SESSION structure instance and releases all system resources owned by that session instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-899">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-899">Parameters</span></span>

- <span data-ttu-id="e9bb8-900">**session_ptr** Wskaźnik do wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-900">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-901">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-901">Return Values</span></span>

- <span data-ttu-id="e9bb8-902">**NX_SUCCESS** (0x00) Pomyślne zainicjowanie sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-902">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="e9bb8-903">**NX_PTR_ERROR** (0x07) Próbował użyć nieprawidłowego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-903">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-904">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-904">Allowed From</span></span>

<span data-ttu-id="e9bb8-905">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-905">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-906">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-906">Example</span></span>

```C
/* Delete TLS session.  */
status =  nx_secure_tls_session_delete(&tls_session);


/* If status is NX_SUCCESS the TLS Session was successfully deleted.  */
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-907">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-907">See Also</span></span>

- <span data-ttu-id="e9bb8-908">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="e9bb8-908">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="e9bb8-909">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="e9bb8-909">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="e9bb8-910">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="e9bb8-910">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="e9bb8-911">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="e9bb8-911">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="e9bb8-912">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="e9bb8-912">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="e9bb8-913">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="e9bb8-913">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="e9bb8-914">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="e9bb8-914">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_end"></a><span data-ttu-id="e9bb8-915">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="e9bb8-915">nx_secure_tls_session_end</span></span>

<span data-ttu-id="e9bb8-916">Zakończenie aktywnej bezpiecznej sesji TLS netx</span><span class="sxs-lookup"><span data-stu-id="e9bb8-916">End an active NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-917">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-917">Prototype</span></span>

```C
UINT  nx_secure_tls_session_end(NX_SECURE_TLS_SESSION *session_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="e9bb8-918">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-918">Description</span></span>

<span data-ttu-id="e9bb8-919">Ta usługa kończy sesję TLS reprezentowaną przez wystąpienie struktury NX_SECURE_TLS_SESSION, wysyłając komunikat TLS CloseNotify do hosta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-919">This service ends a TLS session represented by an NX_SECURE_TLS_SESSION structure instance by sending the TLS CloseNotify message to the remote host.</span></span> <span data-ttu-id="e9bb8-920">Następnie usługa czeka, aż host zdalny odpowie własnym komunikatem CloseNotify.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-920">The service then waits for the remote host to respond with its own CloseNotify message.</span></span>

<span data-ttu-id="e9bb8-921">Jeśli host zdalny nie wyśle komunikatu CloseNotify, usługa TLS uzna ten błąd za błąd i możliwe naruszenie zabezpieczeń, dlatego sprawdzenie wartości zwracanej jest ważne dla bezpiecznego połączenia.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-921">If the remote host does not send a CloseNotify message, TLS considers this an error and a possible security breach, so checking the return value is important for a secure connection.</span></span> <span data-ttu-id="e9bb8-922">Parametr **wait_option** służy do kontrolowania, jak długo usługa powinna czekać na odpowiedź przed zwróceniem kontrolki do wątku wywołującego.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-922">The **wait_option** parameter can be used to control how long the service should wait for the response before returning control to the calling thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-923">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-923">Parameters</span></span>

- <span data-ttu-id="e9bb8-924">**session_ptr** Wskaźnik do wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-924">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="e9bb8-925">**wait_option** Wskazuje, jak długo usługa powinna czekać na odpowiedź z hosta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-925">**wait_option** Indicates how long the service should wait for the response from the remote host.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-926">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-926">Return Values</span></span>

- <span data-ttu-id="e9bb8-927">**NX_SUCCESS** (0x00) Pomyślne zainicjowanie sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-927">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="e9bb8-928">**NX_SECURE_TLS_NO_CLOSE_RESPONSE** (0x113) Nie otrzymał odpowiedzi z hosta zdalnego przed przekierowywem.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-928">**NX_SECURE_TLS_NO_CLOSE_RESPONSE** (0x113) Did not receive a response from the remote host before timing out.</span></span>
- <span data-ttu-id="e9bb8-929">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Nie można przydzielić pakietu w celu wysłania komunikatu CloseNotify.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-929">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Could not allocate a packet to send the CloseNotify message.</span></span>
- <span data-ttu-id="e9bb8-930">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Nie można wysłać komunikatu CloseNotify za pośrednictwem gniazda TCP.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-930">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Could not send the CloseNotify message over the TCP socket.</span></span>
- <span data-ttu-id="e9bb8-931">**NX_PTR_ERROR** (0x07) Próbowano użyć nieprawidłowego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-931">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-932">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-932">Allowed From</span></span>

<span data-ttu-id="e9bb8-933">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-933">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-934">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-934">Example</span></span>

```C
/* End TLS session.  */
status =  nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the TLS Session was successfully ended.  */
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-935">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-935">See Also</span></span>

- <span data-ttu-id="e9bb8-936">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="e9bb8-936">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="e9bb8-937">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="e9bb8-937">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="e9bb8-938">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="e9bb8-938">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="e9bb8-939">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="e9bb8-939">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="e9bb8-940">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="e9bb8-940">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="e9bb8-941">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="e9bb8-941">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="e9bb8-942">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="e9bb8-942">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_packet_buffer_set"></a><span data-ttu-id="e9bb8-943">nx_secure_tls_session_packet_buffer_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-943">nx_secure_tls_session_packet_buffer_set</span></span>

<span data-ttu-id="e9bb8-944">Ustawianie buforu ponownego zestawu pakietów dla bezpiecznej sesji protokołu TLS netx</span><span class="sxs-lookup"><span data-stu-id="e9bb8-944">Set the packet reassembly buffer for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-945">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-945">Prototype</span></span>

```C
UINT  nx_secure_tls_session_packet_buffer_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    UCHAR *buffer_ptr,
                                    ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="e9bb8-946">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-946">Description</span></span>

<span data-ttu-id="e9bb8-947">Ta usługa kojarzy bufor ponownego skojarzenia pakietów z sesją protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-947">This service associates a packet reassembly buffer to a TLS session.</span></span> <span data-ttu-id="e9bb8-948">W celu odszyfrowania i analizy przychodzących rekordów protokołu TLS dane w każdym rekordzie muszą zostać zebrane z podstawowych pakietów TCP.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-948">In order to decrypt and parse incoming TLS records, the data in each record must be assembled from the underlying TCP packets.</span></span> <span data-ttu-id="e9bb8-949">Rekordy TLS mogą mieć rozmiar do 16 KB (chociaż zwykle są znacznie mniejsze), więc mogą nie mieścić się w jednym pakiecie TCP.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-949">TLS records can be up to 16KB in size (though typically are much smaller) so may not fit into a single TCP packet.</span></span>

<span data-ttu-id="e9bb8-950">Jeśli wiesz, że rozmiar komunikatu przychodzącego będzie mniejszy niż limit rekordów TLS 16 KB, rozmiar buforu może być mniejszy, ale w celu obsługi nieznanych danych przychodzących bufor powinien być tak duży, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-950">If you know the incoming message size will be smaller than the TLS record limit of 16KB, the buffer size can be made smaller, but in order to handle unknown incoming data the buffer should be made as large as possible.</span></span> <span data-ttu-id="e9bb8-951">Jeśli przychodzący rekord jest większy niż podany bufor, sesja TLS zakończy się błędem.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-951">If an incoming record is larger than the supplied buffer, the TLS session will end with an error.</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-952">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-952">Parameters</span></span>

- <span data-ttu-id="e9bb8-953">**session_ptr** Wskaźnik do wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-953">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="e9bb8-954">**buffer_ptr** Wskaźnik do bufora dla protokołu TLS do użycia na użytek ponownego zsembmbly pakietów.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-954">**buffer_ptr** Pointer to buffer for TLS to use for packet reassembly.</span></span>
- <span data-ttu-id="e9bb8-955">**buffer_size** Rozmiar dostarczonego buforu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-955">**buffer_size** Size of the supplied buffer in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-956">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-956">Return Values</span></span>

- <span data-ttu-id="e9bb8-957">**NX_SUCCESS** (0x00) Pomyślne zainicjowanie sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-957">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="e9bb8-958">**NX_INVALID_PARAMETERS** (0x4D) Nieprawidłowy bufor lub wskaźnik sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-958">**NX_INVALID_PARAMETERS** (0x4D) Invalid buffer or TLS session pointer.</span></span>
- <span data-ttu-id="e9bb8-959">**NX_PTR_ERROR** (0x07) Próbował użyć nieprawidłowego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-959">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-960">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-960">Allowed From</span></span>

<span data-ttu-id="e9bb8-961">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-961">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-962">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-962">Example</span></span>

```C
/* Buffer for TLS packet reassembly. */
UCHAR tls_packet_buffer[16384];
/* Assign buffer to TLS session.  */
status =  nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                  sizeof(tls_packet_buffer));


/* If status is NX_SUCCESS the buffer was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-963">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-963">See Also</span></span>

- <span data-ttu-id="e9bb8-964">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="e9bb8-964">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="e9bb8-965">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="e9bb8-965">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="e9bb8-966">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="e9bb8-966">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="e9bb8-967">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="e9bb8-967">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="e9bb8-968">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="e9bb8-968">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="e9bb8-969">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="e9bb8-969">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="e9bb8-970">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="e9bb8-970">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_protocol_version_override"></a><span data-ttu-id="e9bb8-971">nx_secure_tls_session_protocol_version_override</span><span class="sxs-lookup"><span data-stu-id="e9bb8-971">nx_secure_tls_session_protocol_version_override</span></span>

<span data-ttu-id="e9bb8-972">Zastąp domyślną wersję protokołu TLS dla bezpiecznej sesji protokołu TLS NetX</span><span class="sxs-lookup"><span data-stu-id="e9bb8-972">Override the default TLS protocol version for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-973">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-973">Prototype</span></span>

```C
UINT  nx_secure_tls_session_protocol_version_override(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              USHORT protocol_version);
```

### <a name="description"></a><span data-ttu-id="e9bb8-974">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-974">Description</span></span>

<span data-ttu-id="e9bb8-975">Ta usługa zastępuje domyślną (najnowszą) wersję protokołu TLS używaną przez określoną sesję.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-975">This service overrides the default (newest) TLS protocol version used by a particular session.</span></span> <span data-ttu-id="e9bb8-976">Dzięki temu funkcja NetX Secure TLS może używać starszej wersji TLS dla określonej sesji TLS bez wyłączania nowszej wersji TLS w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-976">This enables NetX Secure TLS to use an older version of TLS for a specific TLS Session without disabling newer TLS versions at compile time.</span></span> <span data-ttu-id="e9bb8-977">Może to być przydatne w aplikacjach, które mogą wymagać komunikacji ze starszym hostem, który nie obsługuje najnowszej wersji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-977">This may be useful in applications that may need to communicate with an older host that does not support the newest version of TLS.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e9bb8-978">*Od wersji 5.11SP3 usługa NetX Secure TLS obsługuje zabezpieczenia RFC 7507 (patrz uwaga poniżej), a wszelkie przesłonięcia starszej wersji za pomocą tego interfejsu API spowodują, że rezerwowy scSV zostanie wysłany w aplikacji ClientHello. Jeśli serwer obsługuje nowszą wersję zabezpieczeń TLS, a rezerwowy scSV jest uwzględniony w aplikacji ClientHello, ten serwer przerwać ugodę TLS z alertem "Nieodpowiednie rezerwowe". ScSV jest wysyłany tylko wtedy, gdy przesłonięcie wersji jest starszą wersją TLS niż jest włączona (np. jeśli zastąpisz wersję TLS 1.2, nie będą wysyłane żadne scSV).*</span><span class="sxs-lookup"><span data-stu-id="e9bb8-978">*As of version 5.11SP3, NetX Secure TLS supports RFC 7507 (see note below) and any override to an older version with this API will result in a fallback SCSV being sent in the ClientHello. If the server supports a newer version of TLS and the fallback SCSV is included in the ClientHello, that server will abort the TLS handshake with an "Inappropriate Fallback" alert. The SCSV is only sent when the version override is an older version of TLS than is enabled (e.g. if you override the version to TLS 1.2, no SCSV will be sent).*</span></span>

<span data-ttu-id="e9bb8-979">Prawidłowe wartości parametru protocol_version to następujące makra: NX_SECURE_TLS_VERSION_TLS_1_0, NX_SECURE_TLS_VERSION_TLS_1_1 i NX_SECURE_TLS_VERSION_TLS_1_2.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-979">Valid values for the protocol_version parameter are the following macros: NX_SECURE_TLS_VERSION_TLS_1_0, NX_SECURE_TLS_VERSION_TLS_1_1, and NX_SECURE_TLS_VERSION_TLS_1_2.</span></span>

<span data-ttu-id="e9bb8-980">Makra NX_SECURE_TLS_DISABLE_TLS_1_1 i NX_SECURE_TLS_ENABLE_TLS_1_0 mogą służyć do kontrolowania wersji TLS, które są kompilowane w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-980">The macros NX_SECURE_TLS_DISABLE_TLS_1_1 and NX_SECURE_TLS_ENABLE_TLS_1_0 can be used to control the versions of TLS that are compiled into the application.</span></span> <span data-ttu-id="e9bb8-981">TLS w wersji 1.2 jest zawsze włączony.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-981">TLS version 1.2 is always enabled.</span></span>

<span data-ttu-id="e9bb8-982">Należy pamiętać, że jeśli host zdalny nie obsługuje podanej wersji, połączenie nie powiedzie się — tylko dostarczona wersja zastąpienia będzie negocjowana przez zabezpieczenia TLS netx.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-982">Note that if the remote host does not support the supplied version, the connection will fail – only the supplied override version will be negotiated by NetX Secure TLS.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e9bb8-983">RFC 7507: TLS Fallback SCSV.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-983">RFC 7507: TLS Fallback SCSV.</span></span> <span data-ttu-id="e9bb8-984">Ten dokument RFC został wprowadzony w celu ograniczenia problemu z zabezpieczeniami, który był pierwotnie spowodowany przez serwery, które nieprawidłowo obsługiowały negocjacje obniżania poziomu protokołu, a zamiast tego odrzucały prawidłowe komunikaty ClientHello.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-984">This RFC was introduced to mitigate a security problem that was originally caused by servers that improperly handled protocol downgrade negotiation and instead rejected otherwise valid ClientHello messages.</span></span> <span data-ttu-id="e9bb8-985">Aby zachować zgodność z tymi starymi serwerami, niektóre aplikacje klienckie TLS zaczęły ponawiać próby nieudanych prób ugodowych z i starszą wersją TLS (np. TLS 1.2 nie powiodło się, więc wypróbuj TLS 1.1).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-985">In an attempt to remain compatible with these old servers, some TLS client applications started to retry failed handshakes with and older TLS version (e.g. TLS 1.2 failed so try TLS 1.1).</span></span> <span data-ttu-id="e9bb8-986">To obejście wprowadziło jednak nowy problem — osoba atakująca może wymusić obniżenie poziomu klienta przez sztuczne wprowadzenie błędu sieci lub pakietu powodującego niepowodzenie połączenia z serwerem — nawet jeśli serwer obsługiwał nowszą wersję protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-986">This workaround however introduced a new problem – an attacker could force a client to downgrade by artificially introducing a network or packet error causing the server connection to fail – even when the server supported the newer TLS version.</span></span> <span data-ttu-id="e9bb8-987">Dzięki spadkowi do starszej wersji osoba atakująca może wykorzystać słabe strony w tej wersji (w szczególności SSLv3<sup>21</sup> jest słaba do ataku POODLE).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-987">By downgrading to an older version the attacker could exploit weaknesses in that version (SSLv3<sup>21</sup> in particular is weak to the POODLE attack).</span></span> <span data-ttu-id="e9bb8-988">Aby zapobiec tej sytuacji, w dokumencie RFC 7507 wprowadzenie "rezerwowego scSV", pseudo-ciphersuite<sup>22</sup> wysyłanego w aplikacji ClientHello, który powiadamia serwer TLS, gdy klient TLS korzysta z wersji TLS, która nie jest najnowszą wersją, która obsługuje.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-988">To prevent this situation, RFC 7507 introdued the "fallback SCSV," a pseudo-ciphersuite<sup>22</sup> sent in the ClientHello that notifies a TLS server when a TLS client is using a TLS version that is not the newest version it supports.</span></span> <span data-ttu-id="e9bb8-989">Dzięki temu serwer obsługujący nowszą wersję może odrzucić klienta ClientHello zawierającego rezerwowy scSV i zapobiec sukcesowi ataku na starszą wersję.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-989">This way, a server that supports a newer version can reject a ClientHello containing the fallback SCSV and prevent the downgrade attack from succeeding.</span></span>

21. <span data-ttu-id="e9bb8-990">NetX Secure nie implementuje SSLv3 ze względu na istnienie znanych poważnych słabych stron, takich jak POODLE.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-990">NetX Secure does not implement SSLv3 due to the existence of known serious weaknesses such as POODLE.</span></span>

22. <span data-ttu-id="e9bb8-991">Pseudoszyfrowanie (SCSV, Signaling Cipher Suite Value) to zastrzeżony numer szyfru, który służy do sygnalizowania włączonych implementacji TLS dotyczących funkcji, które nie były dostępne w starszych wersjach TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-991">A pseudo-ciphersuite, or SCSV (Signaling Cipher Suite Value), is a reserved ciphersuite number that is used to signal enabled TLS implementations about features that were not available in older TLS versions.</span></span> <span data-ttu-id="e9bb8-992">Przykładami są rezerwowy scSV i TLS_EMPTY_RENEGOTIATION_INFO_SCSV (RFC 5746).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-992">The fallback SCSV and the TLS_EMPTY_RENEGOTIATION_INFO_SCSV (RFC 5746) are examples.</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-993">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-993">Parameters</span></span>

- <span data-ttu-id="e9bb8-994">**session_ptr** Wskaźnik do wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-994">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="e9bb8-995">**protocol_version** Makro wersji TLS dla określonej wersji TLS do użycia.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-995">**protocol_version** TLS version macro for the specific TLS version to use.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-996">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-996">Return Values</span></span>

- <span data-ttu-id="e9bb8-997">**NX_SUCCESS** (0x00) Pomyślna zmiana stanu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-997">**NX_SUCCESS** (0x00) Successful state change.</span></span>
- <span data-ttu-id="e9bb8-998">**NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-998">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="e9bb8-999">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) Znana, ale nieobsługiwana wersja TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-999">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) Known but unsupported TLS version.</span></span>
- <span data-ttu-id="e9bb8-1000">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Nieprawidłowa wersja protokołu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1000">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Invalid protocol version.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-1001">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1001">Allowed From</span></span>

<span data-ttu-id="e9bb8-1002">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1002">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-1003">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1003">Example</span></span>

```C
/* Set the protocol version to be used to TLSv1.1. */
status = nx_secure_tls_session_protocol_version_override(&tls_session,
                                              NX_SECURE_TLS_VERSION_TLS_1_1);

/* This TLS Session will use TLSv1.1 for the handshake and TLS session. */
status = nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-1004">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1004">See Also</span></span>

- <span data-ttu-id="e9bb8-1005">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1005">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="e9bb8-1006">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1006">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_receive"></a><span data-ttu-id="e9bb8-1007">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1007">nx_secure_tls_session_receive</span></span>

<span data-ttu-id="e9bb8-1008">Odbieranie danych z bezpiecznej sesji TLS netx</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1008">Receive data from a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-1009">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1009">Prototype</span></span>

```C
UINT  nx_secure_tls_session_receive(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET **packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="e9bb8-1010">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1010">Description</span></span>

<span data-ttu-id="e9bb8-1011">Ta usługa odbiera dane z określonej aktywnej sesji protokołu TLS, obsługujący odszyfrowywanie tych danych przed dostarczeniem ich do wywołującego w NX_PACKET parametru.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1011">This service receives data from the specified active TLS session, handling the decryption of that data before providing it to the caller in the NX_PACKET parameter.</span></span> <span data-ttu-id="e9bb8-1012">Jeśli w określonej sesji nie ma żadnych danych w kolejce, wywołanie zostanie wstrzymane na podstawie podanej opcji oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1012">If no data is queued in the specified session, the call suspends based on the supplied wait option.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e9bb8-1013">*Jeśli NX_SUCCESS zostanie zwrócony, aplikacja jest odpowiedzialna za zwolnienie odebranego pakietu, gdy nie jest już potrzebny.*</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1013">*If NX_SUCCESS is returned, the application is responsible for releasing the received packet when it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-1014">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1014">Parameters</span></span>

- <span data-ttu-id="e9bb8-1015">**session_ptr** Wskaźnik do wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1015">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="e9bb8-1016">**packet_ptr** Wskaźnik do przydzielonego wskaźnika pakietu TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1016">**packet_ptr** Pointer to an allocated TLS packet pointer.</span></span>
- <span data-ttu-id="e9bb8-1017">**wait_option** Wskazuje, jak długo usługa powinna czekać na pakiet z hosta zdalnego przed zwróceniem.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1017">**wait_option** Indicates how long the service should wait for a packet from the remote host before returning.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-1018">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1018">Return Values</span></span>

- <span data-ttu-id="e9bb8-1019">**NX_SUCCESS** (0x00) Pomyślne zainicjowanie sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1019">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="e9bb8-1020">**NX_NO_PACKET** (0x01) Nie odebrano żadnych danych.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1020">**NX_NO_PACKET** (0x01) No data received.</span></span>
- <span data-ttu-id="e9bb8-1021">**NX_NOT_CONNECTED** (0x38) Bazowe gniazdo TCP nie jest już połączone.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1021">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="e9bb8-1022">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Odebrany komunikat zakończył się niepowodzeniem podczas sprawdzania skrótu uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1022">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) A received message failed an authentication hash check.</span></span>
- <span data-ttu-id="e9bb8-1023">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Odebrany komunikat zawierał w nagłówku nieznaną wersję protokołu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1023">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received message contained an unknown protocol version in its header.</span></span>
- <span data-ttu-id="e9bb8-1024">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Odebrała alert TLS z hosta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1024">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Received a TLS alert from the remote host.</span></span>
- <span data-ttu-id="e9bb8-1025">**NX_PTR_ERROR** (0x07) Próbowano użyć nieprawidłowego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1025">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="e9bb8-1026">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) Dostarczona sesja TLS nie została zainicjowana.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1026">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-1027">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1027">Allowed From</span></span>

<span data-ttu-id="e9bb8-1028">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1028">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-1029">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1029">Example</span></span>

```C
/* Receive a packet from an active TLS session previously created and started with
nx_secure_tls_session_start. Wait until a packet is received, blocking otherwise.
*/
status =  nx_secure_tls_session_receive(&tls_session, &packet_ptr,
NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the received packet is pointed to by  "packet_ptr". */
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-1030">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1030">See Also</span></span>

- <span data-ttu-id="e9bb8-1031">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1031">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="e9bb8-1032">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1032">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="e9bb8-1033">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1033">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="e9bb8-1034">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1034">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="e9bb8-1035">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1035">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="e9bb8-1036">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1036">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="e9bb8-1037">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1037">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="e9bb8-1038">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1038">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_renegotiate_callback_set"></a><span data-ttu-id="e9bb8-1039">nx_secure_tls_session_renegotiate_callback_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1039">nx_secure_tls_session_renegotiate_callback_set</span></span>

<span data-ttu-id="e9bb8-1040">Przypisywanie wywołania zwrotnego, które będzie wywoływane na początku ponownego negocjowania sesji</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1040">Assign a callback that will be invoked at the beginning of a session renegotiation</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-1041">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1041">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_renegotiate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(struct NX_SECURE_TLS_SESSION_struct
                  *session));
```

### <a name="description"></a><span data-ttu-id="e9bb8-1042">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1042">Description</span></span>

<span data-ttu-id="e9bb8-1043">Ta usługa przypisuje wywołanie zwrotne do sesji TLS, które będzie wywoływane za każdym razem, gdy pierwszy komunikat ponownego negocjowania sesji zostanie odebrany z hosta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1043">This service assigns a callback to a TLS session that will be invoked whenever the first message of a session renegotiation handshake is received from the remote host.</span></span>

<span data-ttu-id="e9bb8-1044">Funkcja wywołania zwrotnego jest przeznaczona jako powiadomienie do aplikacji o tym, że rozpoczyna się ponowne negocjowanie — aplikacja może zakończyć sesję TLS, zwracając dowolną wartość niezerową z wywołania zwrotnego, co spowoduje zakończenie sesji TLS z błędem.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1044">The callback function is intended as a notification to the application that a renegotiation handshake is beginning – the application may choose to terminate the TLS session by returning any non-zero value from the callback which will cause TLS to end the TLS session with an error.</span></span> <span data-ttu-id="e9bb8-1045">Jeśli aplikacja chce kontynuować ponowną negocjację, wywołanie zwrotne powinno zwrócić NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1045">If the application wishes to proceed with the renegotiation, the callback should return NX_SUCCESS.</span></span>

> [!NOTE]
> <span data-ttu-id="e9bb8-1046">*Ze względu na semantykę renegocjowania TLS wywołanie zwrotne zostanie wywołane dla klientów bezpiecznego TLS NetX za każdym razem, gdy z serwera zdalnego zostanie odebrane helloRequest, ale nie wtedy, gdy klient zainicjuje ponowną negocjację. Na serwerach NetX Secure TLS wywołanie zwrotne będzie wywoływane za każdym razem, gdy zostanie odebrane ponowne negocjowanie ClientHello (dowolny klientHello odebrany w kontekście aktywnej sesji TLS). Oznacza to, że wywołanie zwrotne zostanie wywołane niezależnie od tego, czy host zdalny lub aplikacja lokalna zainicjowała ponowne negocjowanie, ponieważ serwer TLS wyśle odpowiedź HelloRequest, na który odpowie klient zdalny.*</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1046">*Due to the semantics of TLS renegotiation, the callback will be invoked for NetX Secure TLS Clients whenever a HelloRequest is received from the remote server, but not when the client initiates the renegotiation. On NetX Secure TLS Servers, the callback will be invoked whenever a renegotiation ClientHello is received (any ClientHello received in the context of an active TLS session). This means that the callback will be invoked whether the remote host or the local application has initiated the renegotiation because the TLS server will send a HelloRequest to which the remote client will respond.*</span></span>

<span data-ttu-id="e9bb8-1047">NetX Secure TLS implementuje rozszerzenie Secure Renegotiation Inidication z specyfikacji RFC 5746, aby zapewnić, że renegocjacja nie będzie podlegała atakom typu man-in-the-middle.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1047">NetX Secure TLS implements the Secure Renegotiation Inidication Extension from RFC 5746 to ensure that renegotiation handshakes are not subject to man-in-the-middle attacks.</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-1048">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1048">Parameters</span></span>

- <span data-ttu-id="e9bb8-1049">**session_ptr** Wskaźnik do wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1049">**session_ptr** Pointer to TLS Session instance.</span></span>
- <span data-ttu-id="e9bb8-1050">**func_ptr** Wskaźnik do funkcji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1050">**func_ptr** Pointer to callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-1051">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1051">Return Values</span></span>

- <span data-ttu-id="e9bb8-1052">**NX_SUCCESS** (0x00) Pomyślne przypisanie wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1052">**NX_SUCCESS** (0x00) Successful assignment of callback.</span></span>
- <span data-ttu-id="e9bb8-1053">**NX_PTR_ERROR** (0x07) Próbowano użyć nieprawidłowego wskaźnika dla funkcji wywołania zwrotnego lub sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1053">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer for the callback function or TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-1054">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1054">Allowed From</span></span>

<span data-ttu-id="e9bb8-1055">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1055">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-1056">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1056">Example</span></span>

```C
/* Simple callback notifying the user that a renegotiation is starting. */
ULONG tls_renegotiation_callback(NX_SECURE_TLS_SESSION *session)
{
    printf("Renegotiation initiated by remote host\n");

    return(NX_SUCCESS);
}

/* Establish a TLS session with a remote host (TLS Client) */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* Set callback for renegotiation notification. */
status = nx_secure_tls_session_renegotiate_callback_set(&tls_session,
                                                tls_renegotiation_callback);
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-1057">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1057">See Also</span></span>

- <span data-ttu-id="e9bb8-1058">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1058">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="e9bb8-1059">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1059">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="e9bb8-1060">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1060">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="e9bb8-1061">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1061">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="e9bb8-1062">nx_secure_tls_session_renegotiate</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1062">nx_secure_tls_session_renegotiate</span></span>

## <a name="nx_secure_tls_session_renegotiate"></a><span data-ttu-id="e9bb8-1063">nx_secure_tls_session_renegotiate</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1063">nx_secure_tls_session_renegotiate</span></span>

<span data-ttu-id="e9bb8-1064">Inicjowanie negocjacji ponownego negocjowania sesji z hostem zdalnym</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1064">Initiate a session renegotiation handshake with the remote host</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-1065">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1065">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_renegotiate (
                  NX_SECURE_TLS_SESSION *tls_session,
                  UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="e9bb8-1066">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1066">Description</span></span>

<span data-ttu-id="e9bb8-1067">Ta usługa inicjuje ponowne *negocjowanie sesji* z połączonym zdalnym hostem TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1067">This service initiates a session *renegotiation* handshake with a connected remote TLS host.</span></span> <span data-ttu-id="e9bb8-1068">Renegocjacja składa się z drugiego ugody TLS w kontekście wcześniej ustanowionej sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1068">A renegotiation consists of a second TLS handshake within the context of a previously-established TLS session.</span></span> <span data-ttu-id="e9bb8-1069">Każdy z nowych komunikatów uściślniania jest szyfrowany przy użyciu sesji TLS do momentu wygenerowania nowych kluczy sesji i wymiany komunikatów ChangeCipherSpec, w którym nowe klucze są używane do szyfrowania wszystkich komunikatów.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1069">Each of the new handshake messages is encrypted using the TLS session until new session keys are generated and ChangeCipherSpec messages are exchanged, at which time the new keys are used to encrypt all messages.</span></span>

<span data-ttu-id="e9bb8-1070">Ponowne negocjowanie można zainicjować w dowolnym momencie po nawiązywaną sesję TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1070">A renegotiation can be initiated at any time once a TLS session is established.</span></span> <span data-ttu-id="e9bb8-1071">Jeśli próba ponownego negocjowania zostanie podjęta podczas ugody TLS lub przed rozpoczęciem sesji TLS, żadna akcja nie zostanie podjęta.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1071">If a renegotiation is attempted during a TLS handshake or before a TLS session is established no action will be taken.</span></span>

> [!NOTE]
> <span data-ttu-id="e9bb8-1072">*Podczas wywoływania tej usługi zostanie wykonane całe uściślnienie TLS, więc czas do ukończenia i zwrócony stan będą się różnić w zależności od bieżących ustawień I parametrów sesji.*</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1072">*An entire TLS handshake will be performed when this service is invoked so the time to completion and returned status will vary depending on the current TLS settings and session parameters.*</span></span>

<span data-ttu-id="e9bb8-1073">NetX Secure TLS implementuje rozszerzenie inidication Secure Renegotiation z RFC 5746, aby zapewnić, że renegocjacja nie będzie podlegać atakom typu man-in-the-middle.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1073">NetX Secure TLS implements the Secure Renegotiation Inidication Extension from RFC 5746 to ensure that renegotiation handshakes are not subject to man-in-the-middle attacks.</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-1074">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1074">Parameters</span></span>

- <span data-ttu-id="e9bb8-1075">**session_ptr** Wskaźnik do wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1075">**session_ptr** Pointer to TLS Session instance.</span></span>
- <span data-ttu-id="e9bb8-1076">**wait_option** Wskazuje, jak długo usługa powinna czekać na pakiet z hosta zdalnego przed zwróceniem.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1076">**wait_option** Indicates how long the service should wait for a packet from the remote host before returning.</span></span> <span data-ttu-id="e9bb8-1077">Jest on przekazywany do wszystkich usług NetX w ramach TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1077">This is passed to all NetX services within TLS.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-1078">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1078">Return Values</span></span>

- <span data-ttu-id="e9bb8-1079">**NX_SUCCESS** (0x00) Pomyślne ponowne negocjowanie.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1079">**NX_SUCCESS** (0x00) Successful renegotiation.</span></span>
- <span data-ttu-id="e9bb8-1080">**NX_NO_PACKET** (0x01) Nie odebrano żadnych danych.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1080">**NX_NO_PACKET** (0x01) No data received.</span></span>
- <span data-ttu-id="e9bb8-1081">**NX_NOT_CONNECTED** (0x38) Bazowe gniazdo TCP nie jest już połączone.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1081">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="e9bb8-1082">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Odebrany komunikat zakończył się niepowodzeniem podczas sprawdzania skrótu uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1082">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) A received message failed an authentication hash check.</span></span>
- <span data-ttu-id="e9bb8-1083">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Odebrany komunikat zawierał w nagłówku nieznaną wersję protokołu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1083">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received message contained an unknown protocol version in its header.</span></span>
- <span data-ttu-id="e9bb8-1084">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Odebrała alert TLS z hosta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1084">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Received a TLS alert from the remote host.</span></span>
- <span data-ttu-id="e9bb8-1085">**NX_SECURE_TLS_RENEGOTIATION_SESSION_INACTIVE** (0x134) Lokalna lub zdalna sesja TLS jest nieaktywna, co uniemożliwia ponowne negocjowanie.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1085">**NX_SECURE_TLS_RENEGOTIATION_SESSION_INACTIVE** (0x134) The local or remote TLS session is inactive, making renegotiation impossible.</span></span>
- <span data-ttu-id="e9bb8-1086">**NX_SECURE_TLS_RENEGOTIATION_FAILURE** (0x13A) host zdalny nie podał rozszerzenia SCSV ani rozszerzenia bezpiecznego ponownego negocjowania i w związku z tym nie można przeprowadzić ponownego negocjowania.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1086">**NX_SECURE_TLS_RENEGOTIATION_FAILURE** (0x13A) The remote host did not provide either the SCSV or Secure Renegotiation Extension and thus renegotiation cannot be performed.</span></span>
- <span data-ttu-id="e9bb8-1087">**NX_PTR_ERROR** (0x07) Próbował użyć nieprawidłowego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1087">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="e9bb8-1088">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) Nie zainicjowano podanej sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1088">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>
- <span data-ttu-id="e9bb8-1089">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Alokacja pakietów bazowych nie powiodła się.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1089">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Underlying packet allocation failed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-1090">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1090">Allowed From</span></span>

<span data-ttu-id="e9bb8-1091">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1091">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-1092">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1092">Example</span></span>

```C
/* Establish a TLS session with a remote host (TLS Client) */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* Setup a client socket connection.  */
status = nx_tcp_client_socket_connect(&tcp_socket, server_ipv4_address,
REMOTE_SERVER_PORT, NX_WAIT_FOREVER);

/* Start the TLS session. */
status = nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);

/* Send some data in the first TLS session. (Check “status” for errors…)*/
status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                       NX_WAIT_FOREVER);
status = nx_packet_data_append(send_packet, "Hello there!\r\n", 14, &pool_0,
                               NX_WAIT_FOREVER);
status = nx_secure_tls_session_send(&tls_session, send_packet,
                                    NX_IP_PERIODIC_RATE);

/* Now renegotiate the session. */
status  = nx_secure_tls_session_renegotiate(&tls_session, NX_WAIT_FOREVER);

/* If status == NX_SUCCESS, new TLS session keys have been generated. */

/* Send some data in the new TLS session. This will be encrypted using the new
   keys. */
status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                       NX_WAIT_FOREVER);
status = nx_packet_data_append(send_packet, "Another message…\r\n", 18, &pool_0,
                               NX_WAIT_FOREVER);
status = nx_secure_tls_session_send(&tls_session, send_packet,
                                    NX_IP_PERIODIC_RATE);
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-1093">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1093">See Also</span></span>

- <span data-ttu-id="e9bb8-1094">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1094">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="e9bb8-1095">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1095">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="e9bb8-1096">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1096">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="e9bb8-1097">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1097">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="e9bb8-1098">nx_secure_tls_session_renegotiation_callback_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1098">nx_secure_tls_session_renegotiation_callback_set</span></span>

## <a name="nx_secure_tls_session_reset"></a><span data-ttu-id="e9bb8-1099">nx_secure_tls_session_reset</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1099">nx_secure_tls_session_reset</span></span>

<span data-ttu-id="e9bb8-1100">Wyczyść i zresetuj bezpieczną sesję TLS netx</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1100">Clear out and reset a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-1101">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1101">Prototype</span></span>

```C
UINT  nx_secure_tls_session_reset (NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="e9bb8-1102">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1102">Description</span></span>

<span data-ttu-id="e9bb8-1103">Ta usługa wyczyszczysz sesję TLS i resetuje stan tak, jakby sesja została właśnie utworzona, aby można było ponownie użyć istniejącego obiektu sesji TLS dla nowej sesji.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1103">This service clears out a TLS session and resets the state as if the session had just been created so an existing TLS session object can be re-used for a new session.</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-1104">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1104">Parameters</span></span>

- <span data-ttu-id="e9bb8-1105">**session_ptr** Wskaźnik do wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1105">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-1106">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1106">Return Values</span></span>

- <span data-ttu-id="e9bb8-1107">**NX_SUCCESS** (0x00) Pomyślne zainicjowanie sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1107">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="e9bb8-1108">**NX_INVALID_PARAMETERS** (0x4D) Nieprawidłowy wskaźnik sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1108">**NX_INVALID_PARAMETERS** (0x4D) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="e9bb8-1109">**NX_PTR_ERROR** (0x07) Próbował użyć nieprawidłowego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1109">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-1110">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1110">Allowed From</span></span>

<span data-ttu-id="e9bb8-1111">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1111">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-1112">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1112">Example</span></span>

```C
/* Reset a TLS session.  */
status =  nx_secure_tls_session_reset(&tls_session);


/* If status is NX_SUCCESS the session was successfully reset and may be reused.*/
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-1113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1113">See Also</span></span>

- <span data-ttu-id="e9bb8-1114">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1114">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="e9bb8-1115">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1115">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="e9bb8-1116">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1116">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="e9bb8-1117">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1117">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="e9bb8-1118">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1118">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="e9bb8-1119">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1119">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="e9bb8-1120">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1120">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_send"></a><span data-ttu-id="e9bb8-1121">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1121">nx_secure_tls_session_send</span></span>

<span data-ttu-id="e9bb8-1122">Wysyłanie danych za pośrednictwem bezpiecznej sesji TLS netx</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1122">Send data through a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-1123">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1123">Prototype</span></span>

```C
UINT  nx_secure_tls_session_send(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET *packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="e9bb8-1124">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1124">Description</span></span>

<span data-ttu-id="e9bb8-1125">Ta usługa wysyła dane w podanym NX_PACKET, używając określonej aktywnej sesji TLS i obsługą szyfrowania tych danych przed wysłaniem ich do hosta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1125">This service sends data in the supplied NX_PACKET, using the specified active TLS session, and handling the encryption of that data before sending it to the remote host.</span></span> <span data-ttu-id="e9bb8-1126">Jeśli rozmiar ostatniego anonsowanego okna odbiornika jest mniejszy niż to żądanie, usługa opcjonalnie wstrzymuje się na podstawie określonych opcji oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1126">If the receiver's last advertised window size is less than this request, the service optionally suspends based on the wait options specified.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e9bb8-1127">*Jeśli nie zostanie zwrócony błąd, aplikacja nie powinna zwalniać pakietu po tym wywołaniu. Spowoduje to nieprzewidywalne wyniki, ponieważ sterownik sieciowy zwolni pakiet po zakończeniu transmisji.*</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1127">*Unless an error is returned, the application should not release the packet after this call. Doing so will cause unpredictable results because the network driver will release the packet after transmission.*</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-1128">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1128">Parameters</span></span>

- <span data-ttu-id="e9bb8-1129">**session_ptr** Wskaźnik do wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1129">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="e9bb8-1130">**packet_ptr** Wskaźnik do pakietu TLS zawierającego dane do wysłania.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1130">**packet_ptr** Pointer to a TLS packet containing data to be sent.</span></span>
- <span data-ttu-id="e9bb8-1131">**wait_option** Definiuje sposób zachowania usługi, jeśli żądanie jest większe niż rozmiar okna odbiornika.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1131">**wait_option** Defines how the service behaves if the request is greater than the window size of the receiver.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-1132">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1132">Return Values</span></span>

- <span data-ttu-id="e9bb8-1133">**NX_SUCCESS** (0x00) Pomyślne zainicjowanie sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1133">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="e9bb8-1134">**NX_NO_PACKET** (0x01) Nie odebrano żadnych danych.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1134">**NX_NO_PACKET** (0x01) No data received.</span></span>
- <span data-ttu-id="e9bb8-1135">**NX_NOT_CONNECTED** (0x38) Bazowe gniazdo TCP nie jest już połączone.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1135">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="e9bb8-1136">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Wysyłanie bazowego gniazda TCP nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1136">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) The underlying TCP socket send failed.</span></span>
- <span data-ttu-id="e9bb8-1137">**NX_PTR_ERROR** (0x07) Próbowano użyć nieprawidłowego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1137">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="e9bb8-1138">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) Dostarczona sesja TLS nie została zainicjowana.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1138">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-1139">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1139">Allowed From</span></span>

<span data-ttu-id="e9bb8-1140">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1140">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-1141">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1141">Example</span></span>

```C
/* Send a packet using an active TLS session previously created and started with
nx_secure_tls_session_start. Wait until a packet is sent, blocking otherwise.   */
status =  nx_secure_tls_session_send(&tls_session, &packet_ptr, NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the packet has been sent. */
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-1142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1142">See Also</span></span>

- <span data-ttu-id="e9bb8-1143">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1143">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="e9bb8-1144">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1144">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="e9bb8-1145">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1145">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="e9bb8-1146">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1146">nx_secure_tls_packet_allocate</span></span>
- <span data-ttu-id="e9bb8-1147">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1147">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="e9bb8-1148">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1148">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="e9bb8-1149">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1149">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="e9bb8-1150">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1150">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="e9bb8-1151">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1151">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_server_callback_set"></a><span data-ttu-id="e9bb8-1152">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1152">nx_secure_tls_session_server_callback_set</span></span>

<span data-ttu-id="e9bb8-1153">Konfigurowanie wywołania zwrotnego dla usługi TLS do wywołania na początku uściślinia serwera TLS</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1153">Set up a callback for TLS to invoke at the beginning of a TLS Server handshake</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-1154">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1154">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_server_callback_set (
                 NX_SECURE_TLS_SESSION *tls_session,
                 ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                   NX_SECURE_TLS_HELLO_EXTENSION
                                   *extensions, UINT num_extensions));
```

### <a name="description"></a><span data-ttu-id="e9bb8-1155">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1155">Description</span></span>

<span data-ttu-id="e9bb8-1156">Ta usługa przypisuje wskaźnik funkcji do sesji TLS, która będzie wywoływana przez usługę TLS po otrzymaniu komunikatu ClientHello serwera TLS Server.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1156">This service assigns a function pointer to a TLS session that TLS will invoke when a TLS Server handshake has received a ClientHello message.</span></span> <span data-ttu-id="e9bb8-1157">Funkcja wywołania zwrotnego umożliwia aplikacji przetwarzanie dowolnych rozszerzeń TLS z odebranego komunikatu ClientHello, które wymagają danych wejściowych lub podejmowania decyzji.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1157">The callback function allows an application to process any TLS extensions from the received ClientHello message that require input or decision making.</span></span>

<span data-ttu-id="e9bb8-1158">Wywołanie zwrotne jest wykonywane z wywołującym blokiem sterowania sesją TLS i tablicą NX_SECURE_TLS_HELLO_EXTENSION obiektów.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1158">The callback is executed with the invoking TLS session control block and an array of NX_SECURE_TLS_HELLO_EXTENSION objects.</span></span> <span data-ttu-id="e9bb8-1159">Tablica obiektów rozszerzeń ma być przekazywana do funkcji pomocnika, która znajdzie i przejmie określone rozszerzenie.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1159">The array of extension objects is intended to be passed into a helper function that will find and parse a specific extension.</span></span> <span data-ttu-id="e9bb8-1160">Aby uzyskać przykładową funkcję pomocnika, która analizuje rozszerzenia TLS podane w komunikatach powitalnych, zobacz *nx_secure_tls_session_sni_extension_parse*.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1160">For an example helper function that parses TLS extensions provided in hello messages, see *nx_secure_tls_session_sni_extension_parse*.</span></span>

<span data-ttu-id="e9bb8-1161">Wywołanie zwrotne serwera może również służyć do wybierania aktywnego certyfikatu tożsamości przy *użyciu nx_secure_tls_active_certificate_set* serwera TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1161">The server callback may also be used to select the active identity certificate using *nx_secure_tls_active_certificate_set* for the TLS Server.</span></span> <span data-ttu-id="e9bb8-1162">Najczęściej występuje to w odpowiedzi na rozszerzenie Oznaczanie nazwy serwera (SNI), które umożliwia klientowi TLS wskazanie serwera, z którym próbuje się skontaktować.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1162">This will most often occur in response to a Server Name Indication (SNI) extension which allows a TLS Client to indicate which server it is attempting to contact.</span></span> <span data-ttu-id="e9bb8-1163">Zobacz odwołania do *nx_secure_tls_session_sni_extension_parse* i *nx_secure_tls_active_certificate_set,* aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1163">See the references for *nx_secure_tls_session_sni_extension_parse* and *nx_secure_tls_active_certificate_set* for more information.</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-1164">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1164">Parameters</span></span>

- <span data-ttu-id="e9bb8-1165">**session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1165">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="e9bb8-1166">**func_ptr** Wskaźnik do funkcji wywołania zwrotnego serwera TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1166">**func_ptr** Pointer to the TLS Server callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-1167">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1167">Return Values</span></span>

- <span data-ttu-id="e9bb8-1168">**NX_SUCCESS** (0x00) Pomyślna alokacja wskaźnika funkcji.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1168">**NX_SUCCESS** (0x00) Successful allocation of Function pointer.</span></span>
- <span data-ttu-id="e9bb8-1169">**NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1169">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-1170">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1170">Allowed From</span></span>

<span data-ttu-id="e9bb8-1171">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1171">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-1172">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1172">Example</span></span>

```C
/* Application-supplied function to map server DNS name to a specific certificate
   ID. The certificate ID is supplied by the application when the certificate is
   added with nx_secure_tls_server_certificate_add. */
UINT application_find_id_by_dns_name(NX_SECURE_X509_DNS_NAME *dns_name)
{
    if(strncmp(dns_name->nx_secure_x509_dns_name, “server_name”,
               dns_name->nx_secure_x509_dns_name_length) == 0)
    {
        /* DNS name matches one we know, return it’s ID. */
        return(0x12);
    }

    /* Unknown DNS name, return 0 to indicate no matching ID found. */
    return(0);
}

/* Callback routine used to process ClientHello extensions and perform other
   runtime actions at the beginning of a TLS handshake (such as selecting an
   identify certificate to provide to the client). */
ULONG tls_server_callback(NX_SECURE_TLS_SESSION *session,
                          NX_SECURE_TLS_HELLO_EXTENSION *extensions, UINT
                          num_extensions)
{
UINT status;
NX_SECURE_X509_DNS_NAME dns_name;
UINT cert_id;
NX_SECURE_X509_CERT *certificate;


    /* Find and parse a Server Name Indication (SNI) extension. */
    status = nx_secure_tls_session_sni_extension_parse(session, extensions,
                                                       num_extensions, &dns_name);

    if(status != NX_SUCCESS && status != NX_SECURE_TLS_EXTENSION_NOT_FOUND)
    {
        /* Parsed an invalid extension, return the error. */
        return(status);
    }

    if(status == NX_SECURE_TLS_EXTENSION_NOT_FOUND)
    {
            /* SNI extension not found, just return success to use the default
               certificate. */
            return(NX_SUCCESS);
    }

    /* Find the application-supplied numeric identifier for the specified DNS
       name provided by the remote client. */
    cert_id = application_find_id_by_dns_name(&dns_name);

    /* If cert_id is 0, just use the default identity certificate added with
       nx_secure_tls_local_certificate_add. */
    if(cert_id != 0)
    {
        /* Application found a matching name, find the certificate in our
           store. */
        status = nx_secure_tls_server_certificate_find(tls_session, &certificate,
                                                       cert_id);

        if(status != NX_SUCCESS)
        {
            /* Didn’t find a valid certificate with the supplied ID. Return an
               error so TLS can shut down the handshake. */
            return(NX_SECURE_TLS_CERTIFICATE_NOT_FOUND);
        }

        /* Set the active identity certificate – the certificate should have been
           added to the local store at application start with
           nx_secure_tls_local_certificate_add. */
        nx_secure_tls_active_certificate_set(session, certificate);
    }

    return(NX_SUCCESS);
}

/* TLS setup routine. */
UINT tls_setup(NX_SECURE_TLS_SESSION *tls_session)
{
        /* Add callback to TLS session.  */
        status =  nx_secure_tls_session_server_callback_set(tls_session,
                                                            server_callback);

        /* If status is NX_SUCCESS the callback was added and will be invoked
           immediately after a ClientHello message is received. */

        return(status);
}
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-1173">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1173">See Also</span></span>

- <span data-ttu-id="e9bb8-1174">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1174">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="e9bb8-1175">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1175">nx_secure_tls_session_client_callback_set</span></span>
- <span data-ttu-id="e9bb8-1176">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1176">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="e9bb8-1177">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1177">nx_secure_tls_session_sni_extension_parse</span></span>
- <span data-ttu-id="e9bb8-1178">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1178">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="e9bb8-1179">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1179">nx_secure_tls_server_certificate_find</span></span>

## <a name="nx_secure_tls_session_sni_extension_parse"></a><span data-ttu-id="e9bb8-1180">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1180">nx_secure_tls_session_sni_extension_parse</span></span>

<span data-ttu-id="e9bb8-1181">Analizowanie rozszerzenia Oznaczanie nazwy serwera (SNI) otrzymanego od klienta TLS</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1181">Parse a Server Name Indication (SNI) extension received from a TLS Client</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-1182">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1182">Prototype</span></span>

```C
UINT  nx_secure_tls_session_sni_extension_parse(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_SECURE_TLS_HELLO_EXTENSION
                                    *extensions,
                                    UINT num_extensions,
                                    NX_SECURE_X509_DNS_NAME *dns_name);
```

### <a name="description"></a><span data-ttu-id="e9bb8-1183">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1183">Description</span></span>

<span data-ttu-id="e9bb8-1184">Ta usługa jest przeznaczona do wywoływania z poziomu wywołania zwrotnego sesji serwera TLS, które jest dodawane do sesji TLS przy użyciu nx_secure_tls_session_server_callback_set.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1184">This service is intended to be called from within a TLS Server session callback, added to a TLS session using nx_secure_tls_session_server_callback_set.</span></span> <span data-ttu-id="e9bb8-1185">Wywołanie zwrotne jest wywoływane po otrzymaniu komunikatu ClientHello od zdalnego klienta TLS i dostarcza tablicę dostępnych rozszerzeń (i liczbę rozszerzeń w tablicy).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1185">The callback is invoked following the reception of a ClientHello message from a remote TLS client and is supplied an array of available extensions (and the number of extensions in the array).</span></span> <span data-ttu-id="e9bb8-1186">Ta tablica i jej długość mogą być przekazywane bezpośrednio do tej procedury, aby określić, czy istnieje rozszerzenie SNI — jeśli nie, zwracany jest element NX_SECURE_TLS_EXTENSION_NOT_FOUND wskazujący po prostu, że klient nie wybrał urządzenia rozszerzenia SNI (nie jest to błąd).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1186">That array and its length can be passed directly to this routine to determine if there is an SNI extension present – if not, NX_SECURE_TLS_EXTENSION_NOT_FOUND is returned indicating simply that the client opted not to provice the SNI extension (this is not an error).</span></span>

<span data-ttu-id="e9bb8-1187">Jeśli rozszerzenie SNI zostanie znalezione, nazwa DNS X.509 dostarczona przez klienta TLS jest zwracana w dns_name struktury.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1187">If the SNI extension is found, the X.509 DNS name supplied by the TLS client is returned in the dns_name structure.</span></span> <span data-ttu-id="e9bb8-1188">Obecnie rozszerzenie SNI dostarcza tylko jeden wpis nazwy DNS, który może być używany przez serwer TLS do określenia certyfikatu tożsamości do wysłania do klienta zdalnego.\*\*</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1188">Currently, the SNI extension only supplies a single DNS name entry, which may be used by the TLS server to determine which identity certificate to send to the remote client.\*\*</span></span>

<span data-ttu-id="e9bb8-1189">Struktura NX_SECURE_X509_DNS_NAME po prostu zawiera nazwę DNS jako ciąg SYSTEMR w polu *nx_secure_x509_dns_name* oraz długość ciągu nazwy w nx_secure_x509_dns_name_length *.*</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1189">The NX_SECURE_X509_DNS_NAME structure simply contains the DNS name as a UCHAR string in the field *nx_secure_x509_dns_name* and the length of the name string in *nx_secure_x509_dns_name_length*.</span></span> <span data-ttu-id="e9bb8-1190">Kontrolka NX_SECURE_X509_DNS_NAME_MAX kontroluje rozmiar buforu nx_secure_x509_dns_name danych.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1190">The macro NX_SECURE_X509_DNS_NAME_MAX controls the size of the nx_secure_x509_dns_name buffer.</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-1191">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1191">Parameters</span></span>

- <span data-ttu-id="e9bb8-1192">**session_ptr** Wskaźnik do wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1192">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="e9bb8-1193">**rozszerzenia** Wskaźnik do tablicy rozszerzeń hello TLS (z wywołania zwrotnego sesji).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1193">**extensions** Pointer to an array of TLS Hello extensions (from session callback).</span></span>
- <span data-ttu-id="e9bb8-1194">**num_extensions** Liczba rozszerzeń w tablicy (z wywołania zwrotnego sesji).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1194">**num_extensions** Number of extensions in array (from session callback).</span></span>
- <span data-ttu-id="e9bb8-1195">**dns_name** Zwróć nazwę DNS podaną w rozszerzeniu SNI.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1195">**dns_name** Return DNS name supplied in the SNI extension.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-1196">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1196">Return Values</span></span>

- <span data-ttu-id="e9bb8-1197">**NX_SUCCESS** (0x00) Pomyślne analizowanie rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1197">**NX_SUCCESS** (0x00) Successful parsing of the extension.</span></span>
- <span data-ttu-id="e9bb8-1198">**NX_PTR_ERROR** (0x07) Nieprawidłowa tablica rozszerzeń lub wskaźnik sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1198">**NX_PTR_ERROR** (0x07) Invalid extensions array or TLS session pointer.</span></span>
- <span data-ttu-id="e9bb8-1199">**NX_SECURE_TLS_EXTENSION_NOT_FOUND** (0x136) nie znaleziono rozszerzenia SNI.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1199">**NX_SECURE_TLS_EXTENSION_NOT_FOUND** (0x136) SNI extension not found.</span></span>
- <span data-ttu-id="e9bb8-1200">**NX_SECURE_TLS_SNI_EXTENSION_INVALID** (0x137) SNI był nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1200">**NX_SECURE_TLS_SNI_EXTENSION_INVALID** (0x137) SNI extension format was invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-1201">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1201">Allowed From</span></span>

<span data-ttu-id="e9bb8-1202">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1202">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-1203">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1203">Example</span></span>

### <a name="see-also"></a><span data-ttu-id="e9bb8-1204">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1204">See Also</span></span>

- <span data-ttu-id="e9bb8-1205">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1205">nx_secure_tls_session_server_callback_set</span></span>
- <span data-ttu-id="e9bb8-1206">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1206">nx_secure_tls_session_client_callback_set</span></span>
- <span data-ttu-id="e9bb8-1207">nx_secure_tls_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1207">nx_secure_tls_server_callback_set</span></span>
- <span data-ttu-id="e9bb8-1208">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1208">nx_secure_tls_active_certificate_set</span></span>

## <a name="nx_secure_tls_session_sni_extension_set"></a><span data-ttu-id="e9bb8-1209">nx_secure_tls_session_sni_extension_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1209">nx_secure_tls_session_sni_extension_set</span></span>

<span data-ttu-id="e9bb8-1210">Ustawianie nazwy DNS Oznaczanie nazwy serwera (SNI) do wysyłania do serwera zdalnego</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1210">Set a Server Name Indication (SNI) extension DNS name to send to a remote Server</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-1211">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1211">Prototype</span></span>

```C
UINT  nx_secure_tls_session_sni_extension_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_SECURE_X509_DNS_NAME *dns_name);
```

### <a name="description"></a><span data-ttu-id="e9bb8-1212">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1212">Description</span></span>

<span data-ttu-id="e9bb8-1213">Ta usługa umożliwia aplikacji klienckiej TLS podanie preferowanej nazwy DNS serwera zdalnemu serwerowi TLS przy użyciu rozszerzenia TLS Oznaczanie nazwy serwera (SNI).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1213">This service allows a TLS Client application to provide a preferred server DNS name to a remote TLS server using the Server Name Indication (SNI) TLS extension.</span></span> <span data-ttu-id="e9bb8-1214">Rozszerzenie SNI umożliwia serwerowi wybranie odpowiedniego certyfikatu tożsamości i parametrów na podstawie preferencji serwera wskazanego przez klienta.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1214">The SNI extension allows the server to select the proper identity certificate and parameters based on the client's indicated server preference.</span></span> <span data-ttu-id="e9bb8-1215">Rozszerzenie SNI obecnie obsługuje tylko jedną nazwę DNS do wysłania, dlatego nazwa pojedyncza parametru.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1215">The SNI extension currently only supports a single DNS name to be sent, hence the singular name parameter.</span></span> <span data-ttu-id="e9bb8-1216">Parametr dns_name musi zostać zainicjowany za pomocą *nx_secure_x509_dns_name_initialize* i będzie zawierać preferowany serwer klienta.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1216">The dns_name parameter must be initialized with *nx_secure_x509_dns_name_initialize* and will contain the client's preferred server.</span></span> <span data-ttu-id="e9bb8-1217">Aby cofnić ustawienia nazwy rozszerzenia, po prostu wywołaj tę usługę z wartością parametru "dns_name" NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1217">To unset the extension name, simply call this service with a "dns_name" parameter value of NX_NULL.</span></span>

<span data-ttu-id="e9bb8-1218">Struktura NX_SECURE_X509_DNS_NAME po prostu zawiera nazwę DNS jako ciąg SYSTEMR w polu *nx_secure_x509_dns_name* oraz długość ciągu nazwy w nx_secure_x509_dns_name_length *.*</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1218">The NX_SECURE_X509_DNS_NAME structure simply contains the DNS name as a UCHAR string in the field  *nx_secure_x509_dns_name* and the length of the name string in *nx_secure_x509_dns_name_length*.</span></span> <span data-ttu-id="e9bb8-1219">Kontrolka NX_SECURE_X509_DNS_NAME_MAX kontroluje rozmiar buforu nx_secure_x509_dns_name danych.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1219">The macro  NX_SECURE_X509_DNS_NAME_MAX controls the size of the nx_secure_x509_dns_name buffer.</span></span>

> [!NOTE]
> <span data-ttu-id="e9bb8-1220">*Ta procedura musi zostać wywołana nx_secure_tls_session_start wywoływania lub ClientHello nie będzie zawierać rozszerzenia SNI.*</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1220">*This routine must be called before nx_secure_tls_session_start is invoked or the ClientHello will not contain the SNI extension.*</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-1221">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1221">Parameters</span></span>

- <span data-ttu-id="e9bb8-1222">**session_ptr** Wskaźnik do wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1222">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="e9bb8-1223">**dns_name** Nazwa DNS dostarczana przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1223">**dns_name** DNS name supplied by the application.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-1224">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1224">Return Values</span></span>

- <span data-ttu-id="e9bb8-1225">**NX_SUCCESS** (0x00) Pomyślne dodanie nazwy serwera DNS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1225">**NX_SUCCESS** (0x00) Successful addition of DNS server name.</span></span>
- <span data-ttu-id="e9bb8-1226">**NX_PTR_ERROR** (0x07) Nieprawidłowa nazwa DNS lub wskaźnik sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1226">**NX_PTR_ERROR** (0x07) Invalid DNS name or TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-1227">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1227">Allowed From</span></span>

<span data-ttu-id="e9bb8-1228">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1228">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-1229">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1229">Example</span></span>

```C
#define TLS_SNI_SERVER_NAME “www.example.com”

NX_SECURE_X509_DNS_NAME dns_name;
NX_SECURE_TLS_SESSION client_tls_session;

/* Application where TLS session is started. */
void main()
{
    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_tls_session_create(&client_tls_session,
                                           &nx_crypto_tls_ciphers,
                                           server_crypto_metadata,
                                           sizeof(server_crypto_metadata));


    /* Initialize the DNS server name we want to send in the SNI extension. */
    nx_secure_x509_dns_name_initialize(&dns_name, TLS_SNI_SERVER_NAME,
                                    strlen(TLS_SNI_SERVER_NAME));

    /* The SNI server name needs to be set prior to starting the TLS session. */
    nx_secure_tls_session_sni_extension_set(&tls_session, &dns_name);

   /* Start TLS session as normal. */
}
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-1230">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1230">See Also</span></span>

- <span data-ttu-id="e9bb8-1231">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1231">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="e9bb8-1232">nx_secure_x509_dns_name_initialize</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1232">nx_secure_x509_dns_name_initialize</span></span>

## <a name="nx_secure_tls_session_start"></a><span data-ttu-id="e9bb8-1233">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1233">nx_secure_tls_session_start</span></span>

<span data-ttu-id="e9bb8-1234">Uruchamianie bezpiecznej sesji TLS netx</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1234">Start a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-1235">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1235">Prototype</span></span>

```C
UINT  nx_secure_tls_session_start(NX_SECURE_TLS_SESSION *session_ptr,
                                  NX_TCP_SOCKET *tcp_socket_ptr,
                                  ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="e9bb8-1236">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1236">Description</span></span>

<span data-ttu-id="e9bb8-1237">Ta usługa uruchamia sesję protokołu TLS przy użyciu dostarczonego bloku sterowania sesją protokołu TLS i połączonego gniazda TCP.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1237">This service starts a TLS session using the supplied TLS session control block and a connected TCP socket.</span></span> <span data-ttu-id="e9bb8-1238">Połączenie TCP musi być już ukończone po pomyślnym wywołaniu nx_tcp_client_socket_connect lub nx_tcp_server_socket_accept.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1238">The TCP connection must already be complete following a successful call to either nx_tcp_client_socket_connect or nx_tcp_server_socket_accept.</span></span>

<span data-ttu-id="e9bb8-1239">Ta usługa określi typ sesji protokołu TLS (klient lub serwer) z gniazda TCP.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1239">This service will determine the type of TLS session (Client or Server) from the TCP socket.</span></span>

<span data-ttu-id="e9bb8-1240">Opcja oczekiwania definiuje sposób zachowania usługi w czasie, gdy trwa uściślanie TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1240">The wait option defines how the service behaves while the TLS handshake is in progress.</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-1241">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1241">Parameters</span></span>

- <span data-ttu-id="e9bb8-1242">**session_ptr** Wskaźnik do wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1242">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="e9bb8-1243">**tcp_socket_ptr** Wskaźnik do połączonego gniazda TCP.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1243">**tcp_socket_ptr** Pointer to a connected TCP socket.</span></span>
- <span data-ttu-id="e9bb8-1244">**wait_option** Definiuje sposób zachowania usługi w czasie, gdy trwa uściślanie TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1244">**wait_option** Defines how the service behaves while the TLS handshake is in progress.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-1245">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1245">Return Values</span></span>

- <span data-ttu-id="e9bb8-1246">**NX_SUCCESS** (0x00) Pomyślne zainicjowanie sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1246">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="e9bb8-1247">**NX_NOT_CONNECTED** (0x38) Bazowe gniazdo TCP nie jest już połączone.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1247">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="e9bb8-1248">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) Odebrany typ komunikatu TLS jest niepoprawny.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1248">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) A received TLS message type is incorrect.</span></span>
- <span data-ttu-id="e9bb8-1249">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) Szyfr dostarczony przez hosta zdalnego nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1249">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) A cipher provided by the remote host is not supported.</span></span>
- <span data-ttu-id="e9bb8-1250">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Przetwarzanie komunikatów podczas uściśniania TLS nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1250">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Message processing during the TLS handshake has failed.</span></span>
- <span data-ttu-id="e9bb8-1251">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Komunikat przychodzący nie może sprawdzić skrótu ADRESU MAC.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1251">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) An incoming message failed a hash MAC check.</span></span>
- <span data-ttu-id="e9bb8-1252">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Nie można wysłać bazowego gniazda TCP.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1252">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) An underlying TCP socket send failed.</span></span>
- <span data-ttu-id="e9bb8-1253">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Komunikat przychodzący miał pole o nieprawidłowej długości.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1253">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) An incoming message had an invalid length field.</span></span>
- <span data-ttu-id="e9bb8-1254">**NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) Przychodzący komunikat ChangeCipherSpec był niepoprawny.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1254">**NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) An incoming ChangeCipherSpec message was incorrect.</span></span>
- <span data-ttu-id="e9bb8-1255">**NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) Przychodzący certyfikat TLS nie można zidentyfikować zdalnego serwera TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1255">**NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) An incoming TLS certificate is unusable for identifying the remote TLS server.</span></span>
- <span data-ttu-id="e9bb8-1256">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) Szyfr klucza publicznego dostarczony przez hosta zdalnego nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1256">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) The public-key cipher provided by the remote host is unsupported.</span></span>
- <span data-ttu-id="e9bb8-1257">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) Host zdalny nie zaznaczył żadnych szyfrów, które są obsługiwane przez stos bezpiecznego szyfrowania TLS netx.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1257">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) The remote host has indicated no ciphersuites that are supported by the NetX Secure TLS stack.</span></span>
- <span data-ttu-id="e9bb8-1258">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Odebrany komunikat TLS miał w nagłówku nieznaną wersję TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1258">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received TLS message had an unknown TLS version in its header.</span></span>
- <span data-ttu-id="e9bb8-1259">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) Odebrany komunikat TLS miał w nagłówku znaną, ale nieobsługiwaną wersję TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1259">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) A received TLS message had a known but unsupported TLS version in its header.</span></span>
- <span data-ttu-id="e9bb8-1260">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Wewnętrzna alokacja pakietów TLS nie powiodła się.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1260">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) An internal TLS packet allocation failed.</span></span>
- <span data-ttu-id="e9bb8-1261">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) host zdalny podał nieprawidłowy certyfikat.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1261">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) The remote host provided an invalid certificate.</span></span>
- <span data-ttu-id="e9bb8-1262">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Host zdalny wysłał alert wskazujący błąd i kończący sesję TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1262">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) The remote host sent an alert indicating an error and ending the TLS session.</span></span>
- <span data-ttu-id="e9bb8-1263">**NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) Wpis w tabeli ciphersuite miał wskaźnik funkcji NULL.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1263">**NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) An entry in the ciphersuite table had a NULL function pointer.</span></span>
- <span data-ttu-id="e9bb8-1264">**NX_SECURE_TLS_INAPPROPRIATE_FALLBACK** (0x146) Zdalny klient TLSHello obejmował rezerwowy system SCSV i dodał rezerwowy dostęp do wersji.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1264">**NX_SECURE_TLS_INAPPROPRIATE_FALLBACK** (0x146) A remote TLS ClientHello included the fallback SCSV andattempted a version fallback.</span></span>
- <span data-ttu-id="e9bb8-1265">**NX_PTR_ERROR** (0x07) Próbował użyć nieprawidłowego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1265">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-1266">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1266">Allowed From</span></span>

<span data-ttu-id="e9bb8-1267">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1267">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-1268">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1268">Example</span></span>

```C
NX_TCP_SOCKET tcp_socket;
NX_SECURE_TLS_SESSION tls_session;
NX_SECURE_X509_CERT certificate;

/* Initialize the TLS session structure. */
nx_secure_tls_session_create(&tls_session,
                              &nx_crypto_tls_ciphers,
                              crypto_metadata,
                              sizeof(crypto_metadata));

/* Setup the TLS packet reassembly buffer. */
status = nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                 sizeof(tls_packet_buffer));

/* Initialize a certificate for the TLS server. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data, 500,
NX_NULL, 0, private_key, 64);

/* If status is NX_SUCCESS, certificate is initialized. */

/* Add the certificate a local certificate to identify this TLS server. */
status = nx_secure_tls_add_local_certificate(&tls_session, &certificate);

/* If status is NX_SUCCESS, certificate was added successfully. */

/* Create and start a TCP socket as a server. */
/* NOTE: This assumes an IP instance called “ip_0” has already been created. */

/* Create a TCP server socket on the previously created IP instance, with normal
   delivery, IP fragmentation enabled, default time to live, a 8192-byte receive
   window, no urgent callback routine, and the "client_disconnect" routine to
   handle disconnection initiated from the other end of the connection.  */
status =  nx_tcp_socket_create(&ip_0, &tcp_socket, "TLS Server Socket", NX_IP_NORMAL,
                               NX_FRAGMENT_OKAY, NX_IP_TIME_TO_LIVE, 8192, NX_NULL,
                               NX_NULL);

/* If status is NX_SUCCESS, the TCP socket was created successfully. */

/* Start up a TCP server socket by listening on port 443 with a listen queue of
   size 5. */
status =  nx_tcp_server_socket_listen(&ip_0, 443, &tcp_socket, 5, NX_NULL);

/* Application main loop. */
while(1)
{
        /* Accept incoming requests on the TCP socket. */
        status =  nx_tcp_server_socket_accept(&tcp_socket, NX_WAIT_FOREVER);

        /* At this point, the TCP socket should be established (but not the TLS
        session yet). */

        /* Start the TLS session on our active TCP socket. */
        status = nx_secure_tls_session_start(&tls_session, &tcp_socket,
                                             NX_WAIT_FOREVER);

        /* At this point, if status is NX_SUCCESS, the TLS session has been
           established.  Application may now send/receive data through this
           channel. */

        /* Send and receive data using the TLS session. */
        /* Allocate TLS packets using nx_secure_tls_packet_allocate, write data with
           nx_packet_data_append, read data with nx_packet_data_extract_offset. */

        /* Send TLS data. */
        nx_secure_tls_session_send(&tls_session, &send_packet, NX_WAIT_FOREVER);

        nx_secure_tls_session_receive(&tls_session, &receive_packet_ptr,
        NX_WAIT_FOREVER);


        /* Once all application data is sent/received, end the TLS session. */
        status = nx_secure_tls_session_end(&tls_session);

        /* If status is NX_SUCCESS, the TLS session has been closed properly. */

        /* Now disconnect the TCP server socket from the client.  */
        nx_tcp_socket_disconnect(&tcp_socket, 200);

        /* Unaccept the TCP server socket.  Note that unaccept is called even if
           disconnect or accept fails.  */
        nx_tcp_server_socket_unaccept(&tcp_socket);

        /* Setup server socket for listening with this socket again.  */
        nx_tcp_server_socket_relisten(&ip_0, 443, &tcp_socket);
}

/* When the server application is shut down, clean up the TLS session. */
nx_secure_tls_session_delete(&tls_session);

/* Finally, clean up the TCP socket as well. */
nx_tcp_socket_delete(&tcp_socket);
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-1269">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1269">See Also</span></span>

- <span data-ttu-id="e9bb8-1270">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1270">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="e9bb8-1271">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1271">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="e9bb8-1272">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1272">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="e9bb8-1273">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1273">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="e9bb8-1274">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1274">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="e9bb8-1275">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1275">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="e9bb8-1276">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1276">nx_secure_tls_packet_allocate</span></span>
- <span data-ttu-id="e9bb8-1277">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1277">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="e9bb8-1278">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1278">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="e9bb8-1279">nx_tcp_socket_accept</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1279">nx_tcp_socket_accept</span></span>
- <span data-ttu-id="e9bb8-1280">nx_tcp_socket_listen</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1280">nx_tcp_socket_listen</span></span>
- <span data-ttu-id="e9bb8-1281">nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1281">nx_tcp_socket_disconnect</span></span>
- <span data-ttu-id="e9bb8-1282">nx_tcp_socket_unaccept</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1282">nx_tcp_socket_unaccept</span></span>
- <span data-ttu-id="e9bb8-1283">nx_tcp_socket_relisten</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1283">nx_tcp_socket_relisten</span></span>
- <span data-ttu-id="e9bb8-1284">nx_tcp_socket_delete</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1284">nx_tcp_socket_delete</span></span>
- <span data-ttu-id="e9bb8-1285">nx_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1285">nx_packet_allocate</span></span>
- <span data-ttu-id="e9bb8-1286">nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1286">nx_packet_data_append</span></span>
- <span data-ttu-id="e9bb8-1287">nx_packet_data_extract_offset</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1287">nx_packet_data_extract_offset</span></span>

## <a name="nx_secure_tls_session_time_function_set"></a><span data-ttu-id="e9bb8-1288">nx_secure_tls_session_time_function_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1288">nx_secure_tls_session_time_function_set</span></span>

<span data-ttu-id="e9bb8-1289">Przypisywanie funkcji znacznika czasu do bezpiecznej sesji TLS netx</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1289">Assign a timestamp function to a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-1290">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1290">Prototype</span></span>

```C
UINT  nx_secure_tls_time_function_set(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              ULONG (*time_func_ptr)(void));
```

### <a name="description"></a><span data-ttu-id="e9bb8-1291">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1291">Description</span></span>

<span data-ttu-id="e9bb8-1292">Ta funkcja konfiguruje wskaźnik funkcji, który będzie wywoływany przez TLS, gdy będzie on wymagał uzyskania bieżącego czasu, który jest używany w różnych komunikatach uściślniania TLS i do weryfikacji certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1292">This function sets up a function pointer that TLS will invoke when it needs to get the current time, which is used in various TLS handshake messages and for verification of certificates.</span></span>

<span data-ttu-id="e9bb8-1293">Oczekuje się, że funkcja zwróci bieżący czas GMT w 32-bitowym formacie systemu UNIX (w sekundach od północy od 1 stycznia 1970 r. czasu UTC, ignorując sekundy przestępne) zgodnie z wymaganiami clientHello w dokumencie TLS RFC 5246.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1293">The function is expected to return the current GMT in UNIX 32-bit format (seconds since the midnight starting Jan 1, 1970, UTC, ignoring leap seconds), as per the ClientHello requirements in the TLS RFC 5246.</span></span>

<span data-ttu-id="e9bb8-1294">Jeśli żadna funkcja znacznika czasu nie zostanie przypisana, zostanie użyta wartość 0 dla sygnatury czasowej w uściśli TLS, a sprawdzanie wygaśnięcia certyfikatu nie będzie działać.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1294">If no timestamp function is assigned, a value of 0 for the timestamp in the TLS handshake will be used and certificate expiration checking will not work.</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-1295">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1295">Parameters</span></span>

- <span data-ttu-id="e9bb8-1296">**session_ptr** Wskaźnik do wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1296">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="e9bb8-1297">**time_func_ptr** Wskaźnik do funkcji, która zwraca bieżący czas (GMT) w 32-bitowym formacie systemu UNIX.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1297">**time_func_ptr** Pointer to a function that returns the current time (GMT) in UNIX 32-bit format.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-1298">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1298">Return Values</span></span>

- <span data-ttu-id="e9bb8-1299">**NX_SUCCESS** (0x00) Pomyślne zainicjowanie sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1299">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="e9bb8-1300">**NX_INVALID_PARAMETERS** (0x4D) Nieprawidłowy wskaźnik sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1300">**NX_INVALID_PARAMETERS** (0x4D) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="e9bb8-1301">**NX_PTR_ERROR** (0x07) Próbował użyć nieprawidłowego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1301">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-1302">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1302">Allowed From</span></span>

<span data-ttu-id="e9bb8-1303">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1303">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-1304">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1304">Example</span></span>

```C
/* This function returns a 32-bit UNIX-style representation of the current GMT
   time. */
ULONG get_gmt_time(void)
{
ULONG time_value;

   /* Platform-specific time calculation goes here… */

   return(time_value);
}

/* Reset a TLS session.  */
status =  nx_secure_tls_timestamp_function_set(&tls_session, get_gmt_time);


/* If status is NX_SUCCESS the function was successfully added.*/
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-1305">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1305">See Also</span></span>

- <span data-ttu-id="e9bb8-1306">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1306">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="e9bb8-1307">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1307">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="e9bb8-1308">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1308">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="e9bb8-1309">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1309">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="e9bb8-1310">nx_secure_tls_session_sendnx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1310">nx_secure_tls_session_sendnx_secure_tls_session_receive</span></span>
- <span data-ttu-id="e9bb8-1311">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1311">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_trusted_certificate_add"></a><span data-ttu-id="e9bb8-1312">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1312">nx_secure_tls_trusted_certificate_add</span></span>

<span data-ttu-id="e9bb8-1313">Dodawanie zaufanego certyfikatu do bezpiecznej sesji TLS netx</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1313">Add trusted certificate to NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-1314">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1314">Prototype</span></span>

```C
UINT  nx_secure_tls_trusted_certificate_add(NX_SECURE_TLS_SESSION
                            *session_ptr, NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a><span data-ttu-id="e9bb8-1315">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1315">Description</span></span>

<span data-ttu-id="e9bb8-1316">Ta usługa dodaje zainicjowane wystąpienie NX_SECURE_X509_CERT struktury do sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1316">This service adds an initialized NX_SECURE_X509_CERT structure instance to a TLS session.</span></span> <span data-ttu-id="e9bb8-1317">Ten certyfikat jest używany przez stos TLS do weryfikowania certyfikatów dostarczonych przez hosta zdalnego podczas uściśniania TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1317">This certificate is used by the TLS stack to verify certificates supplied by the remote host during the TLS handshake.</span></span>

<span data-ttu-id="e9bb8-1318">Zaufane certyfikaty są wymagane w trybie klienta TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1318">Trusted certificates are required for TLS Client mode.</span></span>

<span data-ttu-id="e9bb8-1319">Zaufane certyfikaty są wymagane tylko w trybie serwera TLS, jeśli jest włączone uwierzytelnianie certyfikatu klienta.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1319">Trusted certificates are only required for TLS Server mode if client certificate authentication is enabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-1320">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1320">Parameters</span></span>

- <span data-ttu-id="e9bb8-1321">**session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1321">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="e9bb8-1322">**certificate_ptr** Wskaźnik do zainicjowanych wystąpień certyfikatu TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1322">**certificate_ptr** Pointer to an initialized TLS Certificate instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-1323">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1323">Return Values</span></span>

- <span data-ttu-id="e9bb8-1324">**NX_SUCCESS** (0x00) Pomyślne dodanie certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1324">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="e9bb8-1325">**NX_INVALID_PARAMETERS** (0x4D) Próbowano dodać nieprawidłowy certyfikat.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1325">**NX_INVALID_PARAMETERS** (0x4D) Tried to add an invalid certificate.</span></span>
- <span data-ttu-id="e9bb8-1326">**NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1326">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-1327">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1327">Allowed From</span></span>

<span data-ttu-id="e9bb8-1328">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1328">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-1329">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1329">Example</span></span>

```C
/* Initialize certificate structure. */
status = nx_secure_x509_certificate_initialize(&certificate, certificate_data,
                                               certificate_buffer,
                                               sizeof(certificate_buffer), 500,
                                               private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_trusted_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-1330">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1330">See Also</span></span>

- <span data-ttu-id="e9bb8-1331">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1331">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="e9bb8-1332">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1332">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="e9bb8-1333">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1333">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="e9bb8-1334">nx_secure_tls_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1334">nx_secure_tls_trusted_certificate_remove</span></span>

## <a name="nx_secure_tls_trusted_certificate_remove"></a><span data-ttu-id="e9bb8-1335">nx_secure_tls_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1335">nx_secure_tls_trusted_certificate_remove</span></span>

<span data-ttu-id="e9bb8-1336">Usuwanie zaufanego certyfikatu z bezpiecznej sesji TLS netx</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1336">Remove trusted certificate from NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-1337">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1337">Prototype</span></span>

```C
UINT  nx_secure_tls_trusted_certificate_remove(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    UCHAR *common_name,
                                    UINT common_name_length);
```

### <a name="description"></a><span data-ttu-id="e9bb8-1338">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1338">Description</span></span>

<span data-ttu-id="e9bb8-1339">Ta usługa usuwa zaufany certyfikat z sesji TLS z kluczem w polu Nazwa pospolita w certyfikacie.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1339">This service removes a trusted certificate from a TLS session, keyed on the Common Name field in the certificate.</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-1340">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1340">Parameters</span></span>

- <span data-ttu-id="e9bb8-1341">**session_ptr** Wskaźnik do utworzonego wcześniej wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1341">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="e9bb8-1342">**common_name** Wartość nazwa pospolita certyfikatu do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1342">**common_name** The Common Name value of the certificate to be removed.</span></span>
- <span data-ttu-id="e9bb8-1343">**common_name_length** Długość ciągu nazwy pospolitej.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1343">**common_name_length** The length of the Common Name string.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-1344">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1344">Return Values</span></span>

- <span data-ttu-id="e9bb8-1345">**NX_SUCCESS** (0x00) Pomyślne dodanie certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1345">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="e9bb8-1346">**NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1346">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="e9bb8-1347">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Nie znaleziono certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1347">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Certificate was not found.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-1348">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1348">Allowed From</span></span>

<span data-ttu-id="e9bb8-1349">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1349">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-1350">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1350">Example</span></span>

```C
/* Remove certificate from TLS session.  */
status =  nx_secure_tls_trusted_certificate_remove(&tls_session,
                                                “www.example.com”, 15);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-1351">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1351">See Also</span></span>

- <span data-ttu-id="e9bb8-1352">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1352">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="e9bb8-1353">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1353">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="e9bb8-1354">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1354">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="e9bb8-1355">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1355">nx_secure_tls_trusted_certificate_add</span></span>

## <a name="nx_secure_x509_certificate_initialize"></a><span data-ttu-id="e9bb8-1356">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1356">nx_secure_x509_certificate_initialize</span></span>

<span data-ttu-id="e9bb8-1357">Inicjowanie certyfikatu X.509 dla bezpiecznego TLS NetX</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1357">Initialize X.509 Certificate for NetX Secure TLS</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-1358">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1358">Prototype</span></span>

```C
UINT  nx_secure_x509_certificate_initialize(
                  NX_SECURE_X509_CERT *certificate_ptr,
                  const UCHAR *certificate_data,
                  USHORT certificate_data_length,
                  UCHAR *raw_data_buffer,
                  USHORT buffer_size,
                  const UCHAR *private_key_data,
                  USHORT private_key_data_length,
                  UINT private_key_type);
```

### <a name="description"></a><span data-ttu-id="e9bb8-1359">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1359">Description</span></span>

<span data-ttu-id="e9bb8-1360">Ta usługa inicjuje strukturę NX_SECURE_X509_CERT z zakodowanym binarnie certyfikatem cyfrowym X.509 do użycia w sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1360">This service initializes an NX_SECURE_X509_CERT structure from a binary-encoded X.509 digital certificate for use in a TLS session.</span></span>

<span data-ttu-id="e9bb8-1361">Dane certyfikatu muszą **być prawidłowym** certyfikatem cyfrowym X.509 w formacie binarnym zakodowanym w formacie DER.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1361">The certificate data **must** be a valid X.509 digital certificate in DER-encoded binary format.</span></span> <span data-ttu-id="e9bb8-1362">Dane mogą pochodzić z dowolnego źródła (np. systemu plików, skompilowanego bufora stałego itp.), o ile jest dostarczany wskaźnik FUNKCJI SYSTEMR do tych danych.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1362">The data can some from any source (e.g. file system, compiled constant buffer, etc.) as long as a UCHAR pointer to that data is provided.</span></span>

<span data-ttu-id="e9bb8-1363">Parametr *raw_data_buffer* i jego rozmiar są opcjonalnymi parametrami określającymi dedykowany bufor, do którego dane certyfikatu są kopiowane przed analizą.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1363">The *raw_data_buffer* parameter and its size are optional parameters that specify a dedicated buffer into which the certificate data is copied before parsing.</span></span> <span data-ttu-id="e9bb8-1364">Jeśli raw_data_buffer jako NX_NULL, struktura NX_SECURE_X509_CERT będzie bezpośrednio wskazać tablicę certificate_data (w tym przypadku buffer_size jest ignorowana).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1364">If raw_data_buffer is passed as NX_NULL then the NX_SECURE_X509_CERT structure will point directly into the certificate_data array (buffer_size is ignored in this case).</span></span> <span data-ttu-id="e9bb8-1365">Jeśli raw_data_buffer jako ***NX_NULL,*** nie należy modyfikować danych wskazywanych przez wskaźnik certificate_data lub przetwarzanie certyfikatu prawdopodobnie nie powiedzie się!</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1365">If raw_data_buffer is passed as NX_NULL, ***do not*** modify the data pointed to by the certificate_data pointer or certificate processing will likely fail!</span></span>

<span data-ttu-id="e9bb8-1366">Parametr klucza prywatnego jest używany dla certyfikatów tożsamości lokalnej — klucz prywatny jest używany przez serwery do odszyfrowywania danych klucza przychodzącego od klienta (zaszyfrowanych przy użyciu klucza publicznego serwera) i przez klientów w celu zweryfikowania ich tożsamości na serwerze, gdy serwer zażąda certyfikatu klienta.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1366">The private key parameter is for local identity certificates – the private key is used by servers to decrypt the incoming key data from a client (encrypted using the server's public key) and by clients to verify their identity to a server when the server requests a client certificate.</span></span> <span data-ttu-id="e9bb8-1367">Dodanie klucza prywatnego za pomocą tego interfejsu API spowoduje automatyczne oznaczenie skojarzonego certyfikatu jako certyfikatu tożsamości dla aplikacji TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1367">Adding a private key with this API will automatically mark the associated certificate as being an identity certificate for a TLS application.</span></span> <span data-ttu-id="e9bb8-1368">Podczas inicjowania certyfikatów do innych celów (np. zaufanego magazynu) parametr private_key_data powinien być  przekazywany jako wartość NULL, private_key_data_length  jako 0, *a* private_key_type jako NX_SECURE_X509_KEY_TYPE_NONE.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1368">When initializing certificates for other purposes (e.g. the trusted store), the *private_key_data* parameter should be passed as NULL, the *private_key_data_length* as 0, and the *private_key_type* should be passed as NX_SECURE_X509_KEY_TYPE_NONE.</span></span>

<span data-ttu-id="e9bb8-1369">Parametr *private_key_type* wskazuje formatowanie klucza prywatnego.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1369">The *private_key_type* parameter indicates the formatting of the private key.</span></span> <span data-ttu-id="e9bb8-1370">Jeśli na przykład klucz prywatny jest kluczem prywatnym RSA w formacie PKCS#1 w formacie DER, klucz private_key_type powinien zostać przekazany jako NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER, typ znany netx secure, który zostanie natychmiast przejrzeny i zapisany do późniejszego użycia.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1370">For example, if the private key is a DER-encoded PKCS#1-format RSA private key, the private_key_type should be passed as NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER, a type known to NetX Secure which will be parsed immediately and saved for later use.</span></span>

<span data-ttu-id="e9bb8-1371">Interfejs private_key_type również zdefiniowane przez użytkownika typy kluczy<sup>23</sup> dla platform i aplikacji, które mają określone formaty kluczy lub inne potrzeby.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1371">The private_key_type also supports user-defined key types<sup>23</sup> for platforms and applications that have specific key formats or other needs.</span></span> <span data-ttu-id="e9bb8-1372">Na przykład sprzętowy aparat szyfrowania może używać określonego formatu, który nie jest zrozumiały dla oprogramowania NetX Secure, lub klucz prywatny może być zaszyfrowany lub reprezentowany przez token kryptograficzny, jak w przypadku sprzętu kryptograficznego Trusted Platform Module (TPM) lub PKCS#11.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1372">For example, a hardware-based encryption engine may use a specific format not understood by the NetX Secure software, or a private key may be encrypted or represented by a cryptographic token as might be the case with a Trusted Platform Module (TPM) or PKCS#11 cryptographic hardware.</span></span> <span data-ttu-id="e9bb8-1373">W przypadku użycia typu klucza zdefiniowanego przez użytkownika dane klucza są przekazywane dosłownie do odpowiedniej procedury kryptograficznej — na przykład klucz prywatny RSA zostanie przekazany, bez analizowania lub przetwarzania, bezpośrednio do procedury kryptograficznej RSA dostarczonej do TLS w tabeli szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1373">When a user-defined key type is used, the key data is passed verbatim to the appropriate cryptographic routine - for example, an RSA private key would be passed, without any parsing or processing, directly to the RSA cryptographic routine provided to TLS in the ciphersuite table.</span></span> <span data-ttu-id="e9bb8-1374">Typ klucza zdefiniowanego przez użytkownika jest również przekazywany do procedury kryptograficznych (w przypadku RSA jest to parametr "op").</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1374">The user-defined key type is also passed to the cryptographic routine (in the case of RSA, this is the "op" parameter).</span></span>

<span data-ttu-id="e9bb8-1375">Zakres kluczy zdefiniowanych przez użytkownika obejmuje górną połowę 32-bitowej liczby całkowitej bez znaku, od 0x0001 0000-0xFFFF FFFF.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1375">The range of user-defined keys covers the top half of a 32-bit unsigned integer, from 0x0001 0000-0xFFFF FFFF.</span></span> <span data-ttu-id="e9bb8-1376">Wartości mniejsze niż 0x0001 0000 są zarezerwowane do użycia z użyciem funkcji NetX Secure.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1376">Values less than 0x0001 0000 are reserved for NetX Secure use.</span></span>

<span data-ttu-id="e9bb8-1377">Typy kluczy zdefiniowane przez użytkownika to zaawansowana funkcja, która wymaga niestandardowych procedur kryptograficznych do obsługi nieprzetworzonych danych klucza prywatnego.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1377">User-defined key types are an advanced feature that requires custom cryptographic routines to handle the raw private key data.</span></span> <span data-ttu-id="e9bb8-1378">Jeśli potrzebujesz tej funkcji, skontaktuj się z przedstawicielem firmy Express Logic.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1378">Please contact your Express Logic representative if you have need of this feature.</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-1379">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1379">Parameters</span></span>

- <span data-ttu-id="e9bb8-1380">**certificate_ptr** Wskaźnik do niezainicjowanych wystąpień certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1380">**certificate_ptr** Pointer to an uninitialized X.509 Certificate instance.</span></span>
- <span data-ttu-id="e9bb8-1381">**certificate_data** Wskaźnik do danych binarnych X.509 zakodowanych w formacie DER.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1381">**certificate_data** Pointer to DER-encoded X.509 binary data.</span></span>
- <span data-ttu-id="e9bb8-1382">**raw_data_buffer** Wskaźnik do opcjonalnego buforu danych dedykowanego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1382">**raw_data_buffer** Pointer to optional dedicated certificate data buffer.</span></span>
- <span data-ttu-id="e9bb8-1383">**buffer_size** Rozmiar opcjonalnego buforu danych dedykowanego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1383">**buffer_size** Size of optional dedicated certificate data buffer.</span></span>
- <span data-ttu-id="e9bb8-1384">**certificate_data_length** Długość danych binarnych certyfikatu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1384">**certificate_data_length** Length of certificate binary data in bytes.</span></span>
- <span data-ttu-id="e9bb8-1385">**private_key_data** Wskaźnik do opcjonalnych danych klucza prywatnego.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1385">**private_key_data** Pointer to optional private key data.</span></span>
- <span data-ttu-id="e9bb8-1386">**private_key_data_length** Długość danych klucza prywatnego.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1386">**private_key_data_length** Length of private key data.</span></span>
- <span data-ttu-id="e9bb8-1387">**private_key_type** Identyfikator typu klucza.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1387">**private_key_type** Key type identifier.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-1388">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1388">Return Values</span></span>

- <span data-ttu-id="e9bb8-1389">**NX_SUCCESS** (0x00) Pomyślne dodanie certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1389">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="e9bb8-1390">**NX_PTR_ERROR** (0x07) Próbował użyć nieprawidłowego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1390">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="e9bb8-1391">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) Certificate data did not contain a DER-encoded X.509 certificate (Dane certyfikatu X.509 zakodowane w formacie DER).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1391">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) Certificate data did not contain a DER-encoded X.509 certificate.</span></span>
- <span data-ttu-id="e9bb8-1392">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) nie ma szyfru klucza publicznego, który jest obsługiwany przez usługę NetX Secure.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1392">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) Certificate did not have a public-key cipher that is supported by NetX Secure.</span></span>
- <span data-ttu-id="e9bb8-1393">**NX_SECURE_X509_INVALID_CERTIFICATE_SEQUENCE** (0x186) Klucz prywatny lub certyfikat nie zawiera prawidłowej sekwencji ASN.1.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1393">**NX_SECURE_X509_INVALID_CERTIFICATE_SEQUENCE** (0x186) Private key or certificate did not contain a valid ASN.1 sequence.</span></span>
- <span data-ttu-id="e9bb8-1394">**NX_SECURE_PKCS1_INVALID_PRIVATE_KEY** (0x18A) Podany klucz prywatny nie był prawidłowym kluczem PKCS#1 RSA.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1394">**NX_SECURE_PKCS1_INVALID_PRIVATE_KEY** (0x18A) The provided private key was not a valid PKCS#1 RSA key.</span></span>
- <span data-ttu-id="e9bb8-1395">**NX_SECURE_X509_INVALID_PRIVATE_KEY_TYPE** (0x19D) Podany typ klucza prywatnego nie został zdefiniowany przez użytkownika i nie pasuje do żadnego znanego typu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1395">**NX_SECURE_X509_INVALID_PRIVATE_KEY_TYPE** (0x19D) The private key type provided was not user-defined and did not match any known type.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-1396">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1396">Allowed From</span></span>

<span data-ttu-id="e9bb8-1397">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1397">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-1398">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1398">Example</span></span>

```C
/* Initialize certificate structure. The certificate structure will point directly
   into the certificate_data array since we are passing the raw_data_buffer as
   NX_NULL. This certificate has a private key so it will be used to identify this
   device. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, NX_NULL, 0, private_key, 64, NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);


/* If status is NX_SUCCESS the certificate was successfully initialized.  */
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-1399">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1399">See Also</span></span>

- <span data-ttu-id="e9bb8-1400">nx_secure_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1400">nx_secure_local_certificate_add</span></span>
- <span data-ttu-id="e9bb8-1401">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1401">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="e9bb8-1402">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1402">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="e9bb8-1403">Importowanie certyfikatów X.509 do usługi NetX Secure w rozdziale 3.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1403">Importing X.509 Certificates into NetX Secure in Chapter 3.</span></span>

## <a name="nx_secure_x509_common_name_dns_check"></a><span data-ttu-id="e9bb8-1404">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1404">nx_secure_x509_common_name_dns_check</span></span>

<span data-ttu-id="e9bb8-1405">Sprawdzanie nazwy DNS względem certyfikatu X.509</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1405">Check DNS name against X.509 Certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-1406">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1406">Prototype</span></span>

```C
UINT  nx_secure_x509_common_name_dns_check(
                        NX_SECURE_X509_CERT *certificate,
                        const UCHAR *dns_tld, UINT dns_tld_length);
```

### <a name="description"></a><span data-ttu-id="e9bb8-1407">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1407">Description</span></span>

<span data-ttu-id="e9bb8-1408">Ta usługa sprawdza nazwę pospolitą certyfikatu względem nazwy top-domain name (TLD) dostarczonej przez wywołującego na potrzeby weryfikacji DNS hosta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1408">This service checks a certificate's Common Name against a Top- Domain name (TLD) provided by the caller for the purposes of DNS validation of a remote host.</span></span> <span data-ttu-id="e9bb8-1409">Ta funkcja narzędzia jest przeznaczona do wywoływania z procedury wywołania zwrotnego weryfikacji certyfikatu dostarczonej przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1409">This utility function is intended to be called from within a certificate validation callback routine provided by the application.</span></span> <span data-ttu-id="e9bb8-1410">Nazwa TLD powinna być górną częścią adresu URL używanego do uzyskiwania dostępu do hosta zdalnego ("." ciąg rozdzielany przed pierwszym ukośnikiem).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1410">The TLD name should be the top part of the URL used to access the remote host (the "."-separated string before the first slash).</span></span> <span data-ttu-id="e9bb8-1411">Jeśli nazwa pospolita zawiera symbol wieloznaczny (na przykład example.com), symbol wieloznaczny będzie odpowiadać dowolnej z *tym samym sufiksem. Należy* pamiętać, że tylko pierwszy symbol wieloznaczny (" ") napotkany (odczytywanie od prawej do lewej)  będzie traktowany jako dopasowywanie symboli wieloznacznych — na przykład abc.\*.example.com będzie pasować do dowolnej nazwy kończącej się na ".example.com".</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1411">If the Common Name contains a wildcard (such as *.example.com), the wildcard will match any with the same suffix. Note that only the first wildcard ("*") encountered (reading right-to-left) will be considered for wildcard matching – for example, abc.\*.example.com will match *any* name ending in ".example.com".</span></span>

<span data-ttu-id="e9bb8-1412">Jeśli nazwa pospolita nie pasuje do podanego ciągu, rozszerzenie "subjectAltName" jest analizowane (jeśli istnieje w certyfikacie), a wszystkie wpisy DNSName również są porównywane.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1412">If the Common Name does not match the provided string, the "subjectAltName" extension is parsed (if it exists in the certificate) and any DNSName entries are also compared.</span></span> <span data-ttu-id="e9bb8-1413">Jeśli żaden z tych wpisów nie pasuje, zwracany jest błąd.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1413">If none of those entries match, an error is returned.</span></span>

<span data-ttu-id="e9bb8-1414">Ważne jest, aby zrozumieć format nazwy pospolitej (i wpisów subjectAltName) w oczekiwanych certyfikatach.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1414">It is important to understand the format of the common name (and subjectAltName entries) in expected certificates.</span></span> <span data-ttu-id="e9bb8-1415">Na przykład niektóre certyfikaty mogą używać nieprzetworzowego adresu IP lub symbolu wieloznaowego.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1415">For example, some certificates may use a raw IP address or a wild card.</span></span> <span data-ttu-id="e9bb8-1416">Ciąg TLD systemu DNS musi być sformatowany w taki sposób, aby był on taki, aby był zgodne z oczekiwanymi wartościami w odebranych certyfikatach.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1416">The DNS TLD string must be formatted such that it will match the expected values in received certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-1417">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1417">Parameters</span></span>

- <span data-ttu-id="e9bb8-1418">**certificate_ptr** Wskaźnik do wystąpienia certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1418">**certificate_ptr** Pointer to an X.509 Certificate instance.</span></span>
- <span data-ttu-id="e9bb8-1419">**dns_tld** Top-Level nazwa domeny do porównania.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1419">**dns_tld** Top-Level Domain name to compare against.</span></span>
- <span data-ttu-id="e9bb8-1420">**dns_tld_length** Długość ciągu TLD.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1420">**dns_tld_length** Length of TLD string.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-1421">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1421">Return Values</span></span>

- <span data-ttu-id="e9bb8-1422">**NX_SUCCESS** (0x00) Pomyślne porównanie z nazwą pospolitą lub subjectAltName.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1422">**NX_SUCCESS** (0x00) Successful comparison with Common Name or subjectAltName.</span></span>
- <span data-ttu-id="e9bb8-1423">**NX_SECURE_X509_CERTIFICATE_DNS_MISMATCH** (0x195) Nie znaleziono pasującej nazwy.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1423">**NX_SECURE_X509_CERTIFICATE_DNS_MISMATCH** (0x195) No matching name found.</span></span>
- <span data-ttu-id="e9bb8-1424">**NX_PTR_ERROR** (0x07) Próbowano użyć nieprawidłowego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1424">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-1425">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1425">Allowed From</span></span>

<span data-ttu-id="e9bb8-1426">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1426">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-1427">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1427">Example</span></span>

```C
/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
ULONG status;
UCHAR *tld = “www.example.com”;

    /* Check our DNS TLD against the certificate provided by the
       remote TLS host. */
    status = nx_secure_x509_common_name_dns_check(certificate, tld, strlen(tld));

        if(status != NX_SUCCESS)
        {
            /* TLD did not match any names in the certificate. */
            return(status);
        }

        /* DNS validation and any other checks were successful. */
        return(NX_SUCCESS);
}

…

/* Add callback to TLS session in TLS setup routine.  */
status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                         certificate_callback);
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-1428">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1428">See Also</span></span>

- <span data-ttu-id="e9bb8-1429">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1429">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="e9bb8-1430">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1430">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="e9bb8-1431">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1431">nx_secure_x509_crl_revocation_check</span></span>

## <a name="nx_secure_x509_crl_revocation_check"></a><span data-ttu-id="e9bb8-1432">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1432">nx_secure_x509_crl_revocation_check</span></span>

<span data-ttu-id="e9bb8-1433">Sprawdź certyfikat X.509 względem podanej listy odwołania certyfikatów (CRL)</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1433">Check X.509 Certificate against a supplied Certificate Revocation List (CRL)</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-1434">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1434">Prototype</span></span>

```C
UINT  nx_secure_x509_crl_revocation_check(const UCHAR *crl_data,
                              UINT crl_length,
                              NX_SECURE_X509_CERTIFICATE_STORE *store,
                              NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a><span data-ttu-id="e9bb8-1435">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1435">Description</span></span>

<span data-ttu-id="e9bb8-1436">Ta usługa pobiera listę odwołania certyfikatów zakodowaną w formacie DER i wyszukuje określony certyfikat na tej liście.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1436">This service takes a DER-encoded Certificate Revocation List and searches for a specific certificate in that list.</span></span> <span data-ttu-id="e9bb8-1437">Wystawca listy CRL jest weryfikowany względem podanego magazynu certyfikatów, wystawca listy CRL jest weryfikowany jako taki sam jak wystawca sprawdzanego certyfikatu, a numer seryjny certyfikatu jest używany do przeszukiwania listy odwołanych certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1437">The issuer of the CRL is validated against a supplied certificate store, the CRL issuer is validated to be the same as the one for the certificate being checked, and the serial number of the certificate in question is used to search the revoked certificates list.</span></span> <span data-ttu-id="e9bb8-1438">Jeśli wystawcy są zgodne, podpis jest sprawdzany, a certyfikatu nie ma na liście, wywołanie zostanie pomyślnie wywołane. </span><span class="sxs-lookup"><span data-stu-id="e9bb8-1438">If the issuers match, the signature checks out, and the certificate is **not** present in the list, the call is successful.</span></span> <span data-ttu-id="e9bb8-1439">Wszystkie inne przypadki powodują zwrócenie błędu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1439">All other cases cause an error to be returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-1440">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1440">Parameters</span></span>

- <span data-ttu-id="e9bb8-1441">**crl_data** Wskaźnik do listy CRL zakodowanej w formacie DER.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1441">**crl_data** Pointer to a DER-encoded CRL.</span></span>
- <span data-ttu-id="e9bb8-1442">**crl_length** Długość w bajtach danych listy CRL.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1442">**crl_length** Length in bytes of CRL data.</span></span>
- <span data-ttu-id="e9bb8-1443">**store (sklep)** Wskaźnik do magazynu certyfikatów X.509.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1443">**store** Pointer to an X.509 Certificate store.</span></span>
- <span data-ttu-id="e9bb8-1444">**certificate_ptr** Wskaźnik do wystąpienia certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1444">**certificate_ptr** Pointer to an X.509 Certificate instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-1445">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1445">Return Values</span></span>

- <span data-ttu-id="e9bb8-1446">**NX_SUCCESS** (0x00) Pomyślna weryfikacja, czy certyfikat nie został odwołany.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1446">**NX_SUCCESS** (0x00) Successful validation that the certificate was not revoked.</span></span>
- <span data-ttu-id="e9bb8-1447">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) nie znaleziono certyfikatu wystawcy listy CRL.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1447">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) CRL issuer certificate not found.</span></span>
- <span data-ttu-id="e9bb8-1448">**NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND** 0x11B) Nie znaleziono certyfikatu wystawcy certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1448">**NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND** 0x11B) Certificate issuer certificate not found.</span></span>
- <span data-ttu-id="e9bb8-1449">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Listy CRL ASN.1 zawierała pole o nieprawidłowej długości.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1449">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) The CRL ASN.1 contained an invalid length field.</span></span>
- <span data-ttu-id="e9bb8-1450">**NX_SECURE_X509_UNEXPECTED_ASN1_TAG(0x189)** Listy CRL zawiera nieprawidłowy asn.1.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1450">**NX_SECURE_X509_UNEXPECTED_ASN1_TAG(0x189)** The CRL contained invalid ASN.1.</span></span>
- <span data-ttu-id="e9bb8-1451">**NX_SECURE_X509_CHAIN_VERIFY_FAILURE** (0x18C) Weryfikacja łańcucha certyfikatów nie powiodła się.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1451">**NX_SECURE_X509_CHAIN_VERIFY_FAILURE** (0x18C) A certificate chain verification failed.</span></span>
- <span data-ttu-id="e9bb8-1452">**NX_SECURE_X509_CRL_ISSUER_MISMATCH** (0x197) listy CRL i wystawców certyfikatów nie są zgodne.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1452">**NX_SECURE_X509_CRL_ISSUER_MISMATCH** (0x197) CRL and certificate issuers did not match.</span></span>
- <span data-ttu-id="e9bb8-1453">**NX_SECURE_X509_CRL_SIGNATURE_CHECK_FAILED** 0x198) Podpis listy CRL był nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1453">**NX_SECURE_X509_CRL_SIGNATURE_CHECK_FAILED** 0x198) The CRL signature was invalid.</span></span>
- <span data-ttu-id="e9bb8-1454">**NX_SECURE_X509_CRL_CERTIFICATE_REVOKED** (0x199) Sprawdzany certyfikat został znaleziony na cRL i dlatego został odwołany.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1454">**NX_SECURE_X509_CRL_CERTIFICATE_REVOKED** (0x199) The certificate being checked was found in the CRL and is therefore revoked.</span></span>
- <span data-ttu-id="e9bb8-1455">**NX_PTR_ERROR** (0x07) Próbował użyć nieprawidłowego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1455">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-1456">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1456">Allowed From</span></span>

<span data-ttu-id="e9bb8-1457">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1457">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-1458">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1458">Example</span></span>

```C
/* CRL obtained for the expected certificate issuer through some means (downloaded
   from server manually, obtained from CRL endpoint, etc…) */
const UCHAR *crl_data;
UINT crl_length = 300;

/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
ULONG status;
NX_SECURE_X509_CERTIFICATE_STORE *store;

    /* Obtain a certificate store to check against. In the certificate callback,
       it usually makes the most sense to use the store associated with the TLS
       session. */
    store = &session -> nx_secure_tls_credentials.nx_secure_tls_certificate_store;

    /* Check our certificate against the CRL and TLS certificate store. */
    status = nx_secure_x509_crl_revocation_check(crl, crl_length, store,
                                                 certificate);

        if(status != NX_SUCCESS)
        {
            if(status == NX_SECURE_X509_CRL_CERTIFICATE_REVOKED)
            {
                /* Certificate was revoked. */
               return(status);
            }
            else
            {
               /* CRL was invalid or some other issue. In this case the certificate
                  may still be valid since the CRL itself was a problem. At this
                  point it is up to the application to decide whether to continue
                  with the TLS handshake. For this example, assume certificate is
                  valid (faulty CRL is a possible Denial-of-Service attack).*/
               status = NX_SUCCESS;
        }

    /* Other certificate checking can go here. */

    /* Return status of certificate checks. */
    return(status);
}

…

/* Add callback to TLS session in TLS setup routine.  */
status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                         certificate_callback);
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-1459">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1459">See Also</span></span>

- <span data-ttu-id="e9bb8-1460">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1460">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="e9bb8-1461">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1461">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="e9bb8-1462">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1462">nx_secure_x509_common_name_dns_check</span></span>

## <a name="nx_secure_x509_dns_name_initialize"></a><span data-ttu-id="e9bb8-1463">nx_secure_x509_dns_name_initialize</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1463">nx_secure_x509_dns_name_initialize</span></span>

<span data-ttu-id="e9bb8-1464">Inicjowanie struktury nazw DNS X.509</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1464">Initialize an X.509 DNS name structure</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-1465">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1465">Prototype</span></span>

```C
UINT  nx_secure_x509_dns_name_initialize(
                        NX_SECURE_X509_DNS_NAME *dns_name,
                        const UCHAR *name_string, UINT length);
```

### <a name="description"></a><span data-ttu-id="e9bb8-1466">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1466">Description</span></span>

<span data-ttu-id="e9bb8-1467">Ta usługa inicjuje nazwę DNS X.509 do użycia z niektórymi usługami interfejsu API wymagającymi określonego formatu nazwy.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1467">This service initializes an X.509 DNS name for use with certain API services requiring a specific name format.</span></span> <span data-ttu-id="e9bb8-1468">Na przykład usługa *nx_secure_tls_sni_extension_parse* oczekuje obiektu NX_SECURE_X509_DNS_NAME, aby dopasować nazwę podaną przez hosta zdalnego w rozszerzeniu Oznaczanie nazwy serwera podczas ugody TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1468">For example, the *nx_secure_tls_sni_extension_parse* service expects an NX_SECURE_X509_DNS_NAME object in order to match the name provided by a remote host in the Server Name Indication extension during the TLS handshake.</span></span> <span data-ttu-id="e9bb8-1469">Nazwa DNS jest po prostu ciągiem znaków o długości — maksymalna dozwolona długość nazwy DNS (i rozmiar wewnętrznego buforu w programie NX_SECURE_X509_DNS_NAME) jest kontrolowana przez znak makra NX_SECURE_X509_DNS_NAME_MAX (domyślnie 100 bajtów).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1469">A DNS name is simply a charater string with a length – the maximum allowed length of a DNS name (and the size of the internal buffer in NX_SECURE_X509_DNS_NAME) is controlled by the macro NX_SECURE_X509_DNS_NAME_MAX (default 100 bytes).</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-1470">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1470">Parameters</span></span>

- <span data-ttu-id="e9bb8-1471">**dns_name** Struktura nazw DNS do zainicjowania.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1471">**dns_name** DNS name structure to initialize.</span></span>
- <span data-ttu-id="e9bb8-1472">**name_string** Dane ciągu nazwy DNS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1472">**name_string** DNS name string data.</span></span>
- <span data-ttu-id="e9bb8-1473">**długość** Długość ciągu nazwy.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1473">**length** Length of name string.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-1474">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1474">Return Values</span></span>

- <span data-ttu-id="e9bb8-1475">**NX_SUCCESS** (0x00) Pomyślne inicjowanie.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1475">**NX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="e9bb8-1476">**NX_SECURE_X509_NAME_STRING_TOO_LONG** (0x19E) Podany ciąg nazwy przekroczył NX_SECURE_X509_DNS_NAME_MAX.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1476">**NX_SECURE_X509_NAME_STRING_TOO_LONG** (0x19E) The given name string exceeded NX_SECURE_X509_DNS_NAME_MAX.</span></span>
- <span data-ttu-id="e9bb8-1477">**NX_PTR_ERROR** (0x07) Próbowano użyć nieprawidłowego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1477">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-1478">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1478">Allowed From</span></span>

<span data-ttu-id="e9bb8-1479">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1479">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-1480">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1480">Example</span></span>

```C
NX_SECURE_X509_DNS_NAME dns_name;

/* Initialize DNS name. */
status = nx_secure_x509_dns_name_initialize(&dns_name, “www.example.com”,
                                            strlen(“www.example.com”);

/* Use initialized DNS name to send the Server Name Indication extension to the
   remote TLS server. */
status = nx_secure_tls_session_sni_extension_set(&tls_session, &dns_name);
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-1481">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1481">See Also</span></span>

- <span data-ttu-id="e9bb8-1482">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1482">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="e9bb8-1483">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1483">nx_secure_tls_session_sni_extension_parse</span></span>
- <span data-ttu-id="e9bb8-1484">nx_secure_tls_session_sni_extension_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1484">nx_secure_tls_session_sni_extension_set</span></span>

## <a name="nx_secure_x509_extended_key_usage_extension_parse"></a><span data-ttu-id="e9bb8-1485">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1485">nx_secure_x509_extended_key_usage_extension_parse</span></span>

<span data-ttu-id="e9bb8-1486">Znajdowanie i analizowanie rozszerzenia rozszerzonego użycia klucza X.509 w certyfikacie X.509</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1486">Find and parse an X.509 extended key usage extension in an X.509 certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-1487">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1487">Prototype</span></span>

```C
UINT  nx_secure_x509_extended_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        UINT key_usage);
```

### <a name="description"></a><span data-ttu-id="e9bb8-1488">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1488">Description</span></span>

<span data-ttu-id="e9bb8-1489">Ta usługa jest przeznaczona do wywoływania z poziomu wywołania zwrotnego weryfikacji certyfikatu (zobacz *nx_secure_tls_session_certificate_callback_set).*</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1489">This service is intended to be called from within a certificate verification callback (see *nx_secure_tls_session_certificate_callback_set)*.</span></span> <span data-ttu-id="e9bb8-1490">Wyszuka określony rozszerzony OID użycia klucza w ramach certyfikatu X.509 i zwróci, czy OID jest obecny.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1490">It will search for a specific extended key usage OID within an X.509 certificate and return whether the OID is present.</span></span> <span data-ttu-id="e9bb8-1491">Parametr key_usage jest mapowaniem liczb całkowitych identyfikatorów OID, które są używane wewnętrznie przez netX Secure X.509 i TLS, aby uniknąć przekazywania ciągów identyfikatorów OID o zmiennej długości jako parametrów.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1491">The key_usage parameter is an integer mapping of the OIDs which is used internally by NetX Secure X.509 and TLS to avoid passing the variable-length OID strings as parameters.</span></span>

<span data-ttu-id="e9bb8-1492">Odpowiednie identyfikatory ID dla rozszerzenia rozszerzonego użycia klucza zostały podane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1492">The relevant OIDs for the extended key usage extension are given in the table below.</span></span> <span data-ttu-id="e9bb8-1493">Typowa implementacja klienta TLS, która chce sprawdzić rozszerzone użycie klucza w odebranym certyfikacie serwera TLS, sprawdza istnienie OID NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH — jeśli rozszerzenie jest obecne, ale ten identyfikator OID nie jest, certyfikat zostanie uznany za nieprawidłowy dla identyfikacji hosta jako serwera TLS, a wywołanie zwrotne weryfikacji certyfikatu powinno zwrócić błąd.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1493">A typical TLS Client implementation wishing to check extended key usage in a received TLS server certificate would check for the existence of the OID NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH – if the extension is present but that OID is not, then the certificate would be considered invalid for identifiying the host as a TLS server and the certificate verification callback should return an error.</span></span> <span data-ttu-id="e9bb8-1494">Jeśli brakuje samego rozszerzenia, to aplikacja może kontynuować ugodę TLS.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1494">If the extension itself is missing, then it is up to the application whether or not to proceed with the TLS handshake.</span></span>

<span data-ttu-id="e9bb8-1495">W wywołaniu zwrotym weryfikacji certyfikatu kod powrotny NX_SECURE_X509_KEY_USAGE_ERROR jest zarezerwowany do użycia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1495">In the certificate verification callback, the error return code NX_SECURE_X509_KEY_USAGE_ERROR is reserved for application use.</span></span> <span data-ttu-id="e9bb8-1496">Jeśli wystąpił błąd podczas sprawdzania użycia klucza, ta wartość może zostać zwrócona z wywołania zwrotnego, aby wskazać przyczynę błędu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1496">If there is an error in checking key usage, this value may be returned from the callback to indicate the reason for failure.</span></span>

| <span data-ttu-id="e9bb8-1497">NetX Secure Identifier</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1497">NetX Secure Identifier</span></span>                                | <span data-ttu-id="e9bb8-1498">Wartość OID</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1498">OID Value</span></span>         | <span data-ttu-id="e9bb8-1499">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1499">Description</span></span>                                      |
| --------------------------------------------------------- | --------------------- | ---------------------------------------------------- |
| <span data-ttu-id="e9bb8-1500">NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1500">NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH</span></span>   | <span data-ttu-id="e9bb8-1501">1.3.6.1.5.5.7.3.1</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1501">1.3.6.1.5.5.7.3.1</span></span> | <span data-ttu-id="e9bb8-1502">Certyfikat może służyć do identyfikowania serwera TLS</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1502">Certificate can be used to identify a TLS server</span></span> |
| <span data-ttu-id="e9bb8-1503">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CLIENT_AUTH</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1503">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CLIENT_AUTH</span></span>   | <span data-ttu-id="e9bb8-1504">1.3.6.1.5.5.7.3.2</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1504">1.3.6.1.5.5.7.3.2</span></span> | <span data-ttu-id="e9bb8-1505">Certyfikat może służyć do identyfikowania klienta TLS</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1505">Certificate can be used to identify a TLS client</span></span> |
| <span data-ttu-id="e9bb8-1506">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CODE_SIGNING</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1506">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CODE_SIGNING</span></span>  | <span data-ttu-id="e9bb8-1507">1.3.6.1.5.5.7.3.3</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1507">1.3.6.1.5.5.7.3.3</span></span> | <span data-ttu-id="e9bb8-1508">Certyfikat może służyć do podpisywania kodu</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1508">Certificate can be used to sign code</span></span>             |
| <span data-ttu-id="e9bb8-1509">NX_SECURE_TLS_X509_TYPE_PKIX_KP_EMAIL_PROTECT</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1509">NX_SECURE_TLS_X509_TYPE_PKIX_KP_EMAIL_PROTECT</span></span> | <span data-ttu-id="e9bb8-1510">1.3.6.1.5.5.7.3.4</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1510">1.3.6.1.5.5.7.3.4</span></span> | <span data-ttu-id="e9bb8-1511">Certyfikat może służyć do podpisywania wiadomości e-mail</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1511">Certificate can be used to sign emails</span></span>           |
| <span data-ttu-id="e9bb8-1512">NX_SECURE_TLS_X509_TYPE_PKIX_KP_TIME_STAMPING</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1512">NX_SECURE_TLS_X509_TYPE_PKIX_KP_TIME_STAMPING</span></span> | <span data-ttu-id="e9bb8-1513">1.3.6.1.5.5.7.3.8</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1513">1.3.6.1.5.5.7.3.8</span></span> | <span data-ttu-id="e9bb8-1514">Certyfikat może służyć do podpisywania znaczników czasu</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1514">Certificate can be used to sign timestamps</span></span>       |
| <span data-ttu-id="e9bb8-1515">NX_SECURE_TLS_X509_TYPE_PKIX_KP_OCSP_SIGNING</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1515">NX_SECURE_TLS_X509_TYPE_PKIX_KP_OCSP_SIGNING</span></span>  | <span data-ttu-id="e9bb8-1516">1.3.6.1.5.5.7.3.9</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1516">1.3.6.1.5.5.7.3.9</span></span> | <span data-ttu-id="e9bb8-1517">Certyfikat może służyć do podpisywania odpowiedzi OCSP</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1517">Certificate can be used to sign OCSP responses</span></span>   |

<span data-ttu-id="e9bb8-1518">Identyfikatory ID i mapowania dla rozszerzenia rozszerzonego użycia klucza X.509</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1518">OIDs and mappings for X.509 Extended Key Usage Extension</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-1519">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1519">Parameters</span></span>

- <span data-ttu-id="e9bb8-1520">**certyfikat** Wskaźnik do weryfikowanego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1520">**certificate** Pointer to certificate being verified.</span></span>
- <span data-ttu-id="e9bb8-1521">**key_usage** Mapowanie liczb całkowitych OID z tabeli powyżej.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1521">**key_usage** OID integer mapping from table above.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-1522">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1522">Return Values</span></span>

- <span data-ttu-id="e9bb8-1523">**NX_SUCCESS** (0x00) Znaleziono określony OID użycia klucza.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1523">**NX_SUCCESS** (0x00) Specified key usage OID found.</span></span>
- <span data-ttu-id="e9bb8-1524">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) NAPOTKANO tag ASN.1 (nieobsługiwany certyfikat).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1524">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1 multi-byte tag encountered (unsupported certificate).</span></span>
- <span data-ttu-id="e9bb8-1525">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Napotkano pole Invaild ASN.1 (nieprawidłowy certyfikat).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1525">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Invaild ASN.1 field encountered (invalid certificate).</span></span>
- <span data-ttu-id="e9bb8-1526">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Napotkano nieprawidłową klasę tagów ASN.1 (nieprawidłowy certyfikat).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1526">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Invalid ASN.1 tag class encountered (invalid certificate).</span></span>
- <span data-ttu-id="e9bb8-1527">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Napotkano nieprawidłowe rozszerzenie (nieprawidłowy certyfikat).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1527">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Invalid extension encountered (invalid certificate).</span></span>
- <span data-ttu-id="e9bb8-1528">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) Rozszerzenie Rozszerzone użycie klucza nie zostało znalezione w dostarczonym certyfikacie.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1528">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) The Extended Key Usage extension was not found in the provided certificate.</span></span>
- <span data-ttu-id="e9bb8-1529">**NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1529">**NX_PTR_ERROR** (0x07) Invalid certificate pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-1530">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1530">Allowed From</span></span>

<span data-ttu-id="e9bb8-1531">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1531">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-1532">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1532">Example</span></span>

```C
ULONG certificate_verification_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT* certificate)
{
UINT status;

    /* Extended key usage - look for specific OIDs. */
    status = nx_secure_x509_extended_key_usage_extension_parse(certificate,
                        NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH);

    if(status != NX_SUCCESS)
    {
        if(NX_SECURE_X509_EXT_KEY_USAGE_NOT_FOUND)
        {
            printf("Extended key usage extension not found or specified key usage OID not
                    provided in extension.\n");
            /* The certificate was valid but the specified OID was not found. The
               application can decide whether to continue or abort the TLS handshake. */
            return(NX_SECURE_X509_KEY_USAGE_ERROR);
        }
        else
        {
            /* The extension or certificate was invalid. */
            return(status);
        }
    }

    /* The specified OID was found, return success! */
    return(NX_SUCCESS);
}
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-1533">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1533">See Also</span></span>

- <span data-ttu-id="e9bb8-1534">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1534">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="e9bb8-1535">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1535">nx_secure_x509_key_usage_extension_parse</span></span>
- <span data-ttu-id="e9bb8-1536">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1536">nx_secure_x509_crl_revocation_check</span></span>
- <span data-ttu-id="e9bb8-1537">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1537">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="e9bb8-1538">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1538">nx_secure_x509_extension_find</span></span>

## <a name="nx_secure_x509_extension_find"></a><span data-ttu-id="e9bb8-1539">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1539">nx_secure_x509_extension_find</span></span>

<span data-ttu-id="e9bb8-1540">Znajdowanie i zwracanie rozszerzenia X.509 w certyfikacie X.509</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1540">Find and return an X.509 extension in an X.509 certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-1541">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1541">Prototype</span></span>

```C
UINT  nx_secure_x509_extension_find(
                        NX_SECURE_X509_CERT *certificate,
                        NX_SECURE_X509_EXTENSION *extension,
                        USHORT extension_id);
```

### <a name="description"></a><span data-ttu-id="e9bb8-1542">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1542">Description</span></span>

<span data-ttu-id="e9bb8-1543">Ta usługa jest przeznaczona do wywoływania z poziomu wywołania zwrotnego weryfikacji certyfikatu (zobacz *nx_secure_tls_session_certificate_callback_set)* i jest zaawansowaną usługą X.509.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1543">This service is intended to be called from within a certificate verification callback (see *nx_secure_tls_session_certificate_callback_set)* and is an advanced X.509 service.</span></span>

<span data-ttu-id="e9bb8-1544">Funkcja wyszuka określone rozszerzenie w certyfikacie X.509 na podstawie OID i zwróci, czy OID jest obecny, wraz ze strukturą zawierającą odwołania do odpowiednich nieprzetworzonych danych rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1544">The function will search for a specific extension within an X.509 certificate based on an OID and return whether the OID is present, along with a structure containing references to the relevant raw extension data.</span></span> <span data-ttu-id="e9bb8-1545">Parametr extension_id jest mapowaniem liczb całkowitych identyfikatorów OID, które są używane wewnętrznie przez netx secure X.509 i TLS, aby uniknąć przekazywania ciągów OID o zmiennej długości jako parametrów.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1545">The extension_id parameter is an integer mapping of the OIDs which is used internally by NetX Secure X.509 and TLS to avoid passing the variable-length OID strings as parameters.</span></span>

<span data-ttu-id="e9bb8-1546">Funkcje pomocnika udostępniane dla określonych rozszerzeń (takich jak *nx_secure_x509_key_usage_extension_parse*) wywołują nx_secure_x509_extension_find w celu uzyskania danych rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1546">The helper functions provided for specific extensions (such as *nx_secure_x509_key_usage_extension_parse*) call nx_secure_x509_extension_find internally to obtain the extension data.</span></span>

<span data-ttu-id="e9bb8-1547">Odpowiednie identyfikatory ID dla znanych rozszerzeń X.509 zostały podane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1547">The relevant OIDs for known X.509 extensions are given in the table below.</span></span>

<span data-ttu-id="e9bb8-1548">Struktura NX_SECURE_X509_EXTENSION zawiera wskaźniki do certyfikatu X.509, które umożliwiają funkcji pomocników, takich jak *nx_secure_x509_key_usage_extension_parse,* szybkie dekodowanie nieprzetworzonych danych ASN.1 zakodowanych w formacie DER rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1548">The NX_SECURE_X509_EXTENSION structure contains pointers into the X.509 certificate that allow helper functions such as *nx_secure_x509_key_usage_extension_parse* to quickly decode the raw extension DER-encoded ASN.1 data.</span></span>

<span data-ttu-id="e9bb8-1549">Aby uzyskać informacje na temat określonych rozszerzeń, zobacz RFC 5280 (specyfikacja X.509) lub odwołanie do odpowiednich funkcji pomocnika, jeśli są dostępne.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1549">For information on specific extensions, see RFC 5280 (X.509 specification) or the reference for the appropriate helper functions if available.</span></span>

<span data-ttu-id="e9bb8-1550">Bieżąca wersja netX Secure X.509 ma ograniczoną obsługę rozszerzeń X.509.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1550">The current version of NetX Secure X.509 has limited support for X.509 extensions.</span></span> <span data-ttu-id="e9bb8-1551">Więcej funkcji pomocnika zostanie dodanych w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1551">More helper functions will be added in the future.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e9bb8-1552">*Ta usługa jest zaawansowaną funkcją dla użytkowników zaznajomieni z rozszerzeniami X.509 i asn.1 zakodowanym w formacie DER. Jest on dostarczany w celu umożliwienia tym użytkownikom dostępu do rozszerzeń, dla których program NetX Secure X.509 obecnie nie zapewnia funkcji pomocnika. W przypadku tych rozszerzeń bez funkcji pomocnika musisz samodzielnie analizujeć kodowanie ASN.1 w formacie DER.*</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1552">*This service is an advanced feature for users familiar with X.509 extensions and DER-encoded ASN.1. It is provided to enable those users to access extensions for which NetX Secure X.509 does not currently provide helper functions. For those extensions without helper functions, you will have to parse the raw DER-encoded ASN.1 yourself.*</span></span>

| <span data-ttu-id="e9bb8-1553">NetX Secure Identifier</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1553">NetX Secure Identifier</span></span>                              | <span data-ttu-id="e9bb8-1554">Wartość OID</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1554">OID Value</span></span> | <span data-ttu-id="e9bb8-1555">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1555">Description</span></span>                                                                    | <span data-ttu-id="e9bb8-1556">Funkcja pomocnika?</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1556">Helper function?</span></span> |
| ------------------------------------------------------- | ------------- | ---------------------------------------------------------------------------------- | -------------------- |
| <span data-ttu-id="e9bb8-1557">NX_SECURE_TLS_X509_TYPE_DIRECTORY_ATTRIBUTES</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1557">NX_SECURE_TLS_X509_TYPE_DIRECTORY_ATTRIBUTES</span></span>  | <span data-ttu-id="e9bb8-1558">2.5.29.9</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1558">2.5.29.9</span></span>  | <span data-ttu-id="e9bb8-1559">Atrybuty katalogu — podstawowe atrybuty informacyjne dotyczące podmiotu certyfikatu</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1559">Directory Attributes – basic information attributes about certificate subject</span></span>  | <span data-ttu-id="e9bb8-1560">Nie</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1560">No</span></span>               |
| <span data-ttu-id="e9bb8-1561">NX_SECURE_TLS_X509_TYPE_SUBJECT_KEY_ID</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1561">NX_SECURE_TLS_X509_TYPE_SUBJECT_KEY_ID</span></span>       | <span data-ttu-id="e9bb8-1562">2.5.29.14</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1562">2.5.29.14</span></span> | <span data-ttu-id="e9bb8-1563">Służy do identyfikowania określonego klucza publicznego</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1563">Used to identify a specific public key</span></span>                                         | <span data-ttu-id="e9bb8-1564">Nie</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1564">No</span></span>               |
| <span data-ttu-id="e9bb8-1565">NX_SECURE_TLS_X509_TYPE_KEY_USAGE</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1565">NX_SECURE_TLS_X509_TYPE_KEY_USAGE</span></span>             | <span data-ttu-id="e9bb8-1566">2.5.29.15</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1566">2.5.29.15</span></span> | <span data-ttu-id="e9bb8-1567">Zawiera informacje na temat prawidłowych zastosowań klucza publicznego certyfikatu</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1567">Provides information on valid uses for the certificate public key</span></span>              | <span data-ttu-id="e9bb8-1568">Tak</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1568">Yes</span></span>              |
| <span data-ttu-id="e9bb8-1569">NX_SECURE_TLS_X509_TYPE_SUBJECT_ALT_NAME</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1569">NX_SECURE_TLS_X509_TYPE_SUBJECT_ALT_NAME</span></span>     | <span data-ttu-id="e9bb8-1570">2.5.29.17</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1570">2.5.29.17</span></span> | <span data-ttu-id="e9bb8-1571">Udostępnia alternatywne nazwy DNS do identyfikowania certyfikatu</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1571">Provides alternative DNS names to identify the certificate</span></span>                     | <span data-ttu-id="e9bb8-1572">Tak<sup>24</sup></span><span class="sxs-lookup"><span data-stu-id="e9bb8-1572">Yes<sup>24</sup></span></span>        |
| <span data-ttu-id="e9bb8-1573">NX_SECURE_TLS_X509_TYPE_ISSUER_ALT_NAME</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1573">NX_SECURE_TLS_X509_TYPE_ISSUER_ALT_NAME</span></span>      | <span data-ttu-id="e9bb8-1574">2.5.29.18</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1574">2.5.29.18</span></span> | <span data-ttu-id="e9bb8-1575">Udostępnia alternatywne nazwy DNS do identyfikowania wystawcy certyfikatu</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1575">Provides alternative DNS names to identify the certificate's issuer</span></span>            | <span data-ttu-id="e9bb8-1576">Nie</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1576">No</span></span>               |
| <span data-ttu-id="e9bb8-1577">NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1577">NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS</span></span>     | <span data-ttu-id="e9bb8-1578">2.5.29.19</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1578">2.5.29.19</span></span> | <span data-ttu-id="e9bb8-1579">Zawiera podstawowe informacje o ograniczeniach użycia certyfikatu</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1579">Provides basic certificate usage constraint information</span></span>                        | <span data-ttu-id="e9bb8-1580">Nie</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1580">No</span></span>               |
| <span data-ttu-id="e9bb8-1581">NX_SECURE_TLS_X509_TYPE_NAME_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1581">NX_SECURE_TLS_X509_TYPE_NAME_CONSTRAINTS</span></span>      | <span data-ttu-id="e9bb8-1582">2.5.29.30</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1582">2.5.29.30</span></span> | <span data-ttu-id="e9bb8-1583">Służy do ograniczania nazw certyfikatów do określonych domen</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1583">Used to constrain certificate names to specific domains</span></span>                        | <span data-ttu-id="e9bb8-1584">Nie</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1584">No</span></span>               |
| <span data-ttu-id="e9bb8-1585">NX_SECURE_TLS_X509_TYPE_CRL_DISTRIBUTION</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1585">NX_SECURE_TLS_X509_TYPE_CRL_DISTRIBUTION</span></span>      | <span data-ttu-id="e9bb8-1586">2.5.29.31</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1586">2.5.29.31</span></span> | <span data-ttu-id="e9bb8-1587">Udostępnia adresy URI dla dystrybucji listy CRL</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1587">Provides URIs for CRL distribution</span></span>                                             | <span data-ttu-id="e9bb8-1588">Nie</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1588">No</span></span>               |
| <span data-ttu-id="e9bb8-1589">NX_SECURE_TLS_X509_TYPE_CERTIFICATE_POLICIES</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1589">NX_SECURE_TLS_X509_TYPE_CERTIFICATE_POLICIES</span></span>  | <span data-ttu-id="e9bb8-1590">2.5.29.32</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1590">2.5.29.32</span></span> | <span data-ttu-id="e9bb8-1591">Lista zasad certyfikatów dla dużych systemów PKI</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1591">List of certificate policies for large PKI systems</span></span>                             | <span data-ttu-id="e9bb8-1592">Nie</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1592">No</span></span>               |
| <span data-ttu-id="e9bb8-1593">NX_SECURE_TLS_X509_TYPE_CERT_POLICY_MAPPINGS</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1593">NX_SECURE_TLS_X509_TYPE_CERT_POLICY_MAPPINGS</span></span> | <span data-ttu-id="e9bb8-1594">2.5.29.33</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1594">2.5.29.33</span></span> | <span data-ttu-id="e9bb8-1595">Lista zasad certyfikatów urzędu certyfikacji</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1595">List of CA certificate policies</span></span>                                                | <span data-ttu-id="e9bb8-1596">Nie</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1596">No</span></span>               |
| <span data-ttu-id="e9bb8-1597">NX_SECURE_TLS_X509_TYPE_AUTHORITY_KEY_ID</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1597">NX_SECURE_TLS_X509_TYPE_AUTHORITY_KEY_ID</span></span>     | <span data-ttu-id="e9bb8-1598">2.5.29.35</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1598">2.5.29.35</span></span> | <span data-ttu-id="e9bb8-1599">Służy do identyfikowania określonego klucza publicznego skojarzonego z podpisem certyfikatu</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1599">Used to identify a specific public key associated with a certificate signature</span></span> | <span data-ttu-id="e9bb8-1600">Nie</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1600">No</span></span>               |
| <span data-ttu-id="e9bb8-1601">NX_SECURE_TLS_X509_TYPE_POLICY_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1601">NX_SECURE_TLS_X509_TYPE_POLICY_CONSTRAINTS</span></span>    | <span data-ttu-id="e9bb8-1602">2.5.29.36</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1602">2.5.29.36</span></span> | <span data-ttu-id="e9bb8-1603">Ograniczenia zasad urzędu certyfikacji</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1603">CA policy constraints</span></span>                                                          | <span data-ttu-id="e9bb8-1604">Nie</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1604">No</span></span>               |
| <span data-ttu-id="e9bb8-1605">NX_SECURE_TLS_X509_TYPE_EXTENDED_KEY_USAGE</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1605">NX_SECURE_TLS_X509_TYPE_EXTENDED_KEY_USAGE</span></span>   | <span data-ttu-id="e9bb8-1606">2.5.29.37</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1606">2.5.29.37</span></span> | <span data-ttu-id="e9bb8-1607">Dodatkowe informacje o użyciu klucza oparte na OID</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1607">Additional OID-based key usage information</span></span>                                     | <span data-ttu-id="e9bb8-1608">Tak</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1608">Yes</span></span>              |
| <span data-ttu-id="e9bb8-1609">NX_SECURE_TLS_X509_TYPE_FRESHEST_CRL</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1609">NX_SECURE_TLS_X509_TYPE_FRESHEST_CRL</span></span>          | <span data-ttu-id="e9bb8-1610">2.5.29.46</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1610">2.5.29.46</span></span> | <span data-ttu-id="e9bb8-1611">Zawiera informacje dotyczące uzyskiwania różnicowych listy CRL</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1611">Provides information for obtaining delta CRLs</span></span>                                  | <span data-ttu-id="e9bb8-1612">Nie</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1612">No</span></span>               |
| <span data-ttu-id="e9bb8-1613">NX_SECURE_TLS_X509_TYPE_INHIBIT_ANYPOLICY</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1613">NX_SECURE_TLS_X509_TYPE_INHIBIT_ANYPOLICY</span></span>     | <span data-ttu-id="e9bb8-1614">2.5.29.54</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1614">2.5.29.54</span></span> | <span data-ttu-id="e9bb8-1615">Pole certyfikatu urzędu certyfikacji wskazujące, że nie można użyć anyPolicy</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1615">CA certificate field indicating that AnyPolicy cannot be used</span></span>                  | <span data-ttu-id="e9bb8-1616">Nie</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1616">No</span></span>               |

<span data-ttu-id="e9bb8-1617">Identyfikatory ID i mapowania rozszerzeń X.509</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1617">OIDs and mappings for X.509 Extensions</span></span>

24. <span data-ttu-id="e9bb8-1618">Rozszerzenie SubjectAltName jest analizowane w ramach sprawdzania nazwy DNS w usłudze nx_secure_x509_common_name_dns_check.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1618">The SubjectAltName extension is parsed as part of the DNS name check in the service nx_secure_x509_common_name_dns_check.</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-1619">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1619">Parameters</span></span>

- <span data-ttu-id="e9bb8-1620">**certyfikat** Wskaźnik do weryfikowanego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1620">**certificate** Pointer to certificate being verified.</span></span>
- <span data-ttu-id="e9bb8-1621">**rozszerzenie** Zwracana struktura zawierająca wskaźnik danych rozszerzenia i długość.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1621">**extension** Return structure containing extension data pointer and length.</span></span>
- <span data-ttu-id="e9bb8-1622">**extension_id** Mapowanie liczb całkowitych OID z tabeli powyżej.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1622">**extension_id** OID integer mapping from table above.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-1623">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1623">Return Values</span></span>

- <span data-ttu-id="e9bb8-1624">**NX_SUCCESS** (0x00) Znaleziono określony OID rozszerzenia i zwrócono dane.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1624">**NX_SUCCESS** (0x00) Specified extension OID found and data returned.</span></span>
- <span data-ttu-id="e9bb8-1625">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) NAPOTKANO tag ASN.1 (nieobsługiwany certyfikat).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1625">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1 multi-byte tag encountered (unsupported certificate).</span></span>
- <span data-ttu-id="e9bb8-1626">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Napotkano pole Invaild ASN.1 (nieprawidłowy certyfikat).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1626">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Invaild ASN.1 field encountered (invalid certificate).</span></span>
- <span data-ttu-id="e9bb8-1627">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Napotkano nieprawidłową klasę tagów ASN.1 (nieprawidłowy certyfikat).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1627">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Invalid ASN.1 tag class encountered (invalid certificate).</span></span>
- <span data-ttu-id="e9bb8-1628">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Napotkano nieprawidłowe rozszerzenie</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1628">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Invalid extension encountered</span></span>
- <span data-ttu-id="e9bb8-1629">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) Podany OID rozszerzenia nie został znaleziony w dostarczonym certyfikacie.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1629">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) The given extension OID was not found in the provided certificate.</span></span>
- <span data-ttu-id="e9bb8-1630">**NX_PTR_ERROR** (0x07) Nieprawidłowy certyfikat lub wskaźnik rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1630">**NX_PTR_ERROR** (0x07) Invalid certificate or extension pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-1631">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1631">Allowed From</span></span>

<span data-ttu-id="e9bb8-1632">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1632">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-1633">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1633">Example</span></span>

```C
/* Function to parse a Basic Constraints X.509 extension. */
UINT _basic_constraints_extension_parse(NX_SECURE_X509_CERT *certificate)
{
const UCHAR             *current_buffer;
ULONG                    length;
UINT                     status;
NX_SECURE_X509_EXTENSION extension_data;

    /* Find the Basic Constraints extension in the certificate. */
    status = _nx_secure_x509_extension_find(certificate, &extension_data,
                              NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS);

    /* See if extension present - it might be OK if not present! */
    if (status != NX_SUCCESS)
    {
        return(status);
    }

    /* The extension_data structure now points to the raw extension ASN.1
      (DER-encoded). */
    current_buffer = extension_data.nx_secure_x509_extension_data;
    length = extension_data.nx_secure_x509_extension_data_length;

   /* Extension ASN.1 parsing… */

   return(NX_SUCCESS);
}
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-1634">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1634">See Also</span></span>

- <span data-ttu-id="e9bb8-1635">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1635">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="e9bb8-1636">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1636">nx_secure_x509_key_usage_extension_parse</span></span>
- <span data-ttu-id="e9bb8-1637">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1637">nx_secure_x509_crl_revocation_check</span></span>
- <span data-ttu-id="e9bb8-1638">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1638">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="e9bb8-1639">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1639">nx_secure_x509_extended_key_usage_extension_parse</span></span>

## <a name="nx_secure_x509_key_usage_extension_parse"></a><span data-ttu-id="e9bb8-1640">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1640">nx_secure_x509_key_usage_extension_parse</span></span>

<span data-ttu-id="e9bb8-1641">Znajdowanie i analizowanie rozszerzenia X.509 Key Usage w certyfikacie X.509</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1641">Find and parse an X.509 Key Usage extension in an X.509 certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="e9bb8-1642">Prototype</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1642">Prototype</span></span>

```C
UINT  nx_secure_x509_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        USHORT *bitfield);
```

### <a name="description"></a><span data-ttu-id="e9bb8-1643">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1643">Description</span></span>

<span data-ttu-id="e9bb8-1644">Ta usługa jest przeznaczona do wywoływania z poziomu wywołania zwrotnego weryfikacji certyfikatu (zobacz *nx_secure_tls_session_certificate_callback_set).*</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1644">This service is intended to be called from within a certificate verification callback (see *nx_secure_tls_session_certificate_callback_set)*.</span></span> <span data-ttu-id="e9bb8-1645">Wyszuka rozszerzenie Użycie klucza i jeśli zostanie znalezione, zwróci pole bitowe Użycie klucza w parametrze "bitfield".</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1645">It will search for the Key Usage extension and if found, will return the Key Usage bitfield in the "bitfield" parameter.</span></span>

<span data-ttu-id="e9bb8-1646">Bity zgodnie ze specyfikacją X.509 (RFC 5280) zostały podane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1646">The bits, as defined by the X.509 specification (RFC 5280) are given in the table below.</span></span> <span data-ttu-id="e9bb8-1647">Bitowe AND z odpowiednią maski bitów (i sprawdzanie, czy wartość jest równa zero) daje wartość każdego bitu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1647">A bitwise AND with the appropriate bitmask (and checking for non-zero) will give the value of each bit.</span></span>

<span data-ttu-id="e9bb8-1648">Należy pamiętać, że kodowanie DER pola bitowego eliminuje dodatkowe zera, więc rzeczywista pozycja bitów w nieprzetworzonych danych certyfikatu prawdopodobnie będzie się różnić od ich pozycji w zdekodowanych polach bitowych.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1648">Note that the DER-encoding of the bitfield eliminates extra zeroes so the actual position of the bits in the raw certificate data will likely be different from their positions in the decoded bitfield.</span></span> <span data-ttu-id="e9bb8-1649">Podane maski bitowe są przeznaczone tylko do używać w zdekodowanych polach bitowych zwracanych przez *nx_secure_x509_key_usage_extension_parse,* a nie w nieprzetworzonych danych certyfikatu zakodowanych w formacie DER.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1649">The supplied bitmasks are only intended to be used on the decoded bitfield returned by *nx_secure_x509_key_usage_extension_parse* and not with the raw DER-encoded certificate data.</span></span>

<span data-ttu-id="e9bb8-1650">W wywołaniu zwrotym weryfikacji certyfikatu kod powrotny NX_SECURE_X509_KEY_USAGE_ERROR jest zarezerwowany do użycia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1650">In the certificate verification callback, the error return code NX_SECURE_X509_KEY_USAGE_ERROR is reserved for application use.</span></span> <span data-ttu-id="e9bb8-1651">Jeśli wystąpił błąd podczas sprawdzania użycia klucza, ta wartość może zostać zwrócona z wywołania zwrotnego, aby wskazać przyczynę błędu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1651">If there is an error in checking key usage, this value may be returned from the callback to indicate the reason for failure.</span></span>

| <span data-ttu-id="e9bb8-1652">NetX Secure Identifier</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1652">NetX Secure Identifier</span></span>                            | <span data-ttu-id="e9bb8-1653">Położenie bitowe</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1653">Bit position</span></span> | <span data-ttu-id="e9bb8-1654">Opis</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1654">Description</span></span>                                                                                                                                                  |
| ----------------------------------------------------- | ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="e9bb8-1655">NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1655">NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE</span></span>  | <span data-ttu-id="e9bb8-1656">0</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1656">0</span></span>            | <span data-ttu-id="e9bb8-1657">Certyfikat może służyć do podpisów cyfrowych</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1657">Certificate can be used for digital signatures</span></span>                                                                                                               |
| <span data-ttu-id="e9bb8-1658">NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1658">NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION</span></span>    | <span data-ttu-id="e9bb8-1659">1</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1659">1</span></span>            | <span data-ttu-id="e9bb8-1660">Certyfikat może służyć do weryfikowania podpisów cyfrowych innych niż te dla certyfikatów i list CRL</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1660">Certificate can be used to verify digital signatures other than those for certificates and CRLs</span></span>                                                              |
| <span data-ttu-id="e9bb8-1661">NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1661">NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT</span></span>   | <span data-ttu-id="e9bb8-1662">2</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1662">2</span></span>            | <span data-ttu-id="e9bb8-1663">Certyfikat może służyć do szyfrowania kluczy symetrycznych (transportu kluczy)</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1663">Certificate can be used to encrypt symmetric keys (key transport)</span></span>                                                                                            |
| <span data-ttu-id="e9bb8-1664">NX_SECURE_X509_KEY_USAGE_DATA_ENCIPHERMENT</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1664">NX_SECURE_X509_KEY_USAGE_DATA_ENCIPHERMENT</span></span>  | <span data-ttu-id="e9bb8-1665">3</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1665">3</span></span>            | <span data-ttu-id="e9bb8-1666">Certyfikat może służyć do bezpośredniego szyfrowania nieprzetworzonych danych użytkownika (nietypowe)</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1666">Certificate can be used to directly encrypt raw user data (uncommon)</span></span>                                                                                         |
| <span data-ttu-id="e9bb8-1667">NX_SECURE_X509_KEY_USAGE_KEY_AGREEMENT</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1667">NX_SECURE_X509_KEY_USAGE_KEY_AGREEMENT</span></span>      | <span data-ttu-id="e9bb8-1668">4</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1668">4</span></span>            | <span data-ttu-id="e9bb8-1669">Certyfikat może być używany do umowy kluczy (podobnie jak w przypadku Diffie'ego-Hellmana)</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1669">Certificate can be used for key agreement (as with Diffie-Hellman)</span></span>                                                                                           |
| <span data-ttu-id="e9bb8-1670">NX_SECURE_X509_KEY_USAGE_KEY_CERT_SIGN</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1670">NX_SECURE_X509_KEY_USAGE_KEY_CERT_SIGN</span></span>     | <span data-ttu-id="e9bb8-1671">5</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1671">5</span></span>            | <span data-ttu-id="e9bb8-1672">Certyfikat może służyć do podpisywania i weryfikowania innych certyfikatów (certyfikat jest certyfikatem urzędu certyfikacji lub ICA).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1672">Certificate can be used to sign and verify other certificates (the certificate is a CA or ICA certificate).</span></span>                                                  |
| <span data-ttu-id="e9bb8-1673">NX_SECURE_X509_KEY_USAGE_CRL_SIGN</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1673">NX_SECURE_X509_KEY_USAGE_CRL_SIGN</span></span>           | <span data-ttu-id="e9bb8-1674">6</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1674">6</span></span>            | <span data-ttu-id="e9bb8-1675">Klucz publiczny certyfikatu służy do weryfikowania podpisów list CRL</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1675">Certificate public key is used to verify signatures on CRLs</span></span>                                                                                                  |
| <span data-ttu-id="e9bb8-1676">NX_SECURE_X509_KEY_USAGE_ENCIPHER_ONLY</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1676">NX_SECURE_X509_KEY_USAGE_ENCIPHER_ONLY</span></span>      | <span data-ttu-id="e9bb8-1677">7</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1677">7</span></span>            | <span data-ttu-id="e9bb8-1678">Używany z bitem umowy klucza (bit 4) — po jego skonfigurowaniu klucz certyfikatu może być używany tylko do szyfrowania podczas umowy klucza.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1678">Used with Key Agreement bit (bit 4) – when set, certificate key can only be used to encrypt during key agreement.</span></span> <span data-ttu-id="e9bb8-1679">Niezdefiniowane, jeśli bit umowy klucza nie jest ustawiony.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1679">Undefined if Key Agreement bit is not set.</span></span> |
| <span data-ttu-id="e9bb8-1680">NX_SECURE_X509_KEY_USAGE_DECIPHER_ONLY</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1680">NX_SECURE_X509_KEY_USAGE_DECIPHER_ONLY</span></span>      | <span data-ttu-id="e9bb8-1681">8</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1681">8</span></span>            | <span data-ttu-id="e9bb8-1682">Używany z bitem umowy klucza (bit 4) — w przypadku ustawienia klucz certyfikatu może być używany tylko do odszyfrowywania podczas umowy klucza.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1682">Used with Key Agreement bit (bit 4) – when set, certificate key can only be used to decrypt during key agreement.</span></span> <span data-ttu-id="e9bb8-1683">Niezdefiniowane, jeśli bit umowy klucza nie jest ustawiony.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1683">Undefined if Key Agreement bit is not set.</span></span> |

<span data-ttu-id="e9bb8-1684">Maski bitowe i wartości rozszerzenia X.509 użycia klucza</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1684">Bitmasks and values for X.509 Key Usage Extension</span></span>

### <a name="parameters"></a><span data-ttu-id="e9bb8-1685">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1685">Parameters</span></span>

- <span data-ttu-id="e9bb8-1686">**certyfikat** Wskaźnik do weryfikowanego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1686">**certificate** Pointer to certificate being verified.</span></span>
- <span data-ttu-id="e9bb8-1687">**bitfield** Zwróć całe pola bitowe z rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1687">**bitfield** Return the entire bitfield from the extension.</span></span>

### <a name="return-values"></a><span data-ttu-id="e9bb8-1688">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1688">Return Values</span></span>

- <span data-ttu-id="e9bb8-1689">**NX_SUCCESS** (0x00) Znaleziono rozszerzenie użycia klucza i zwrócono element bitfield.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1689">**NX_SUCCESS** (0x00) Key usage extension found and bitfield returned.</span></span>
- <span data-ttu-id="e9bb8-1690">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) NAPOTKANO tag ASN.1 (nieobsługiwany certyfikat).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1690">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1 multi-byte tag encountered (unsupported certificate).</span></span>
- <span data-ttu-id="e9bb8-1691">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Napotkano pole Invaild ASN.1 (nieprawidłowy certyfikat).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1691">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Invaild ASN.1 field encountered (invalid certificate).</span></span>
- <span data-ttu-id="e9bb8-1692">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Napotkano nieprawidłową klasę tagów ASN.1 (nieprawidłowy certyfikat).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1692">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Invalid ASN.1 tag class encountered (invalid certificate).</span></span>
- <span data-ttu-id="e9bb8-1693">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Napotkano nieprawidłowe rozszerzenie (nieprawidłowy certyfikat).</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1693">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Invalid extension encountered (invalid certificate).</span></span>
- <span data-ttu-id="e9bb8-1694">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B)Rozszerzenie Użycie klucza nie zostało znalezione w dostarczonym certyfikacie.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1694">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B)The Key Usage extension was not found in the provided certificate.</span></span>
- <span data-ttu-id="e9bb8-1695">**NX_PTR_ERROR** (0x07) Nieprawidłowy certyfikat lub wskaźnik pola bitowego.</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1695">**NX_PTR_ERROR** (0x07) Invalid certificate or bitfield pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e9bb8-1696">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1696">Allowed From</span></span>

<span data-ttu-id="e9bb8-1697">Wątki</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1697">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e9bb8-1698">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1698">Example</span></span>

```C
ULONG certificate_verification_callback(NX_SECURE_TLS_SESSION *session,
  NX_SECURE_X509_CERT* certificate)
{
UINT status;
USHORT key_usage_bitfield;

    /* Key usage – extract key usage bitfield. */
    status = nx_secure_x509_key_usage_extension_parse(certificate, &key_usage_bitfield);

   /* Check certificate for a few specific key usage bits. */
   if((key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE) == 0 ||
      (key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION)   == 0 ||
      (key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT)  == 0)
    {
        printf("Expected key usage bitfield bits not set!\n");
        return(NX_SECURE_X509_KEY_USAGE_ERROR);
    }

    /* The specified bits were set, return success! */
    return(NX_SUCCESS);
}
```

### <a name="see-also"></a><span data-ttu-id="e9bb8-1699">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1699">See Also</span></span>

- <span data-ttu-id="e9bb8-1700">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1700">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="e9bb8-1701">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1701">nx_secure_x509_extended_key_usage_extension_parse</span></span>
- <span data-ttu-id="e9bb8-1702">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1702">nx_secure_x509_crl_revocation_check</span></span>
- <span data-ttu-id="e9bb8-1703">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1703">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="e9bb8-1704">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="e9bb8-1704">nx_secure_x509_extension_find</span></span>
