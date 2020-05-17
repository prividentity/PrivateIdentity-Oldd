In this document, prediction process will be documented for each modality. Namely, face, voice, liveness, and fingerprint modalities. This document utilizes NodeJS endpoints, which handles requests and send them back to Python endpoints. 


      let formData = new FormData();
      formData.append('api_key', this.apiKey);

      formData.append('server_extract_embedding', false);
      if (token != null) formData.append('token', token);
      let count = '0';
      predictImages.forEach((element, index) => {
        count++;
        formData.append('images[]', element, count);
      });
      $.ajax({
        type: 'POST',
        contentType: false,
        processData: false,
        url: '/node/generateEmbeddingsAndPredict',
        data: formData,
        error: (response) => {
          console.log('Error:', response);
        }
      })